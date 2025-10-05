##Hill Cypher
hill.py
```
ALPHABET = "abcdefghijklmnopqrstuvwxyz"
a,b = key[0]
c,d = key[1]
return (a * d - b * c) % MOD


def modinv(a, m):
a = a % m
if gcd(a, m) != 1:
return None
t0, t1 = 0, 1
r0, r1 = m, a
while r1 != 0:
q = r0 // r1
r0, r1 = r1, r0 - q * r1
t0, t1 = t1, t0 - q * t1
return t0 % m


def invert_key_2x2(key):
a,b = key[0]
c,d = key[1]
det = (a * d - b * c) % MOD
det_inv = modinv(det, MOD)
if det_inv is None:
return None
inv = [
[( det_inv * d) % MOD, (-det_inv * b) % MOD],
[(-det_inv * c) % MOD, ( det_inv * a) % MOD]
]
return inv


def encrypt_hill_2x2(plaintext, key):
pt = pad_text(clean_text(plaintext), block_size=2)
nums = text_to_nums(pt)
ciphertext_nums = []
for i in range(0, len(nums), 2):
block = nums[i:i+2]
cipher_block = matrix_mul_2x2_vec(key, block)
ciphertext_nums.extend(cipher_block)
return nums_to_text(ciphertext_nums)


def decrypt_hill_2x2(ciphertext, key):
ct = clean_text(ciphertext)
nums = text_to_nums(ct)
inv_key = invert_key_2x2(key)
if inv_key is None:
raise ValueError("Key not invertible mod 26; cannot decrypt.")
plaintext_nums = []
for i in range(0, len(nums), 2):
block = nums[i:i+2]
pt_block = matrix_mul_2x2_vec(inv_key, block)
plaintext_nums.extend(pt_block)
return nums_to_text(plaintext_nums)


def all_invertible_2x2_keys():
for a,b,c,d in product(range(MOD), repeat=4):
det = (a * d - b * c) % MOD
if gcd(det, MOD) == 1:
yield [[a,b],[c,d]]


def english_score(text):
s = text.lower()
score = 0
for w in ('the','and','ing','ion','ed'):
if w in s:
score += 2
for v in 'aeiou':
score += s.count(v) * 0.5
return score


def brute_force_hill_2x2(ciphertext, crib=None, max_results=50):
ct = clean_text(ciphertext)
results = []
crib_clean = clean_text(crib) if crib else None
for key in all_invertible_2x2_keys():
try:
pt = decrypt_hill_2x2(ct, key)
except Exception:
continue
if crib_clean:
if crib_clean in pt:
results.append((key, pt))
else:
score = english_score(pt)
results.append((key, pt, score))
if crib_clean:
return results
results.sort(key=lambda x: x[2], reverse=True)
return results[:max_results]
```
##



