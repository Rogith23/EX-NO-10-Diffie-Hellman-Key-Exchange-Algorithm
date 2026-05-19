# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm
## NAME:ROGITH J
## REGNO:212224040280

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>
#include <math.h>

long long modExp(long long base, long long exp, long long mod) {
    long long result = 1;
    base = base % mod;

    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;

        exp = exp / 2;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long p, g;
    long long a, b;
    long long A, B;
    long long K1, K2;

    printf("Enter a prime number (p): ");
    scanf("%lld", &p);

    printf("Enter a primitive root (g): ");
    scanf("%lld", &g);

    printf("Enter private key of User A: ");
    scanf("%lld", &a);

    printf("Enter private key of User B: ");
    scanf("%lld", &b);

    A = modExp(g, a, p);
    B = modExp(g, b, p);

    printf("\nPublic Key of User A: %lld", A);
    printf("\nPublic Key of User B: %lld", B);

    K1 = modExp(B, a, p);
    K2 = modExp(A, b, p);

    printf("\n\nSecret Key computed by User A: %lld", K1);
    printf("\nSecret Key computed by User B: %lld", K2);

    if (K1 == K2) {
        printf("\n\nKey Exchange Successful! Shared Secret Key is: %lld", K1);
    } else {
        printf("\n\nKey Exchange Failed!");
    }

    return 0;
}
```

## Output:
<img width="605" height="431" alt="image" src="https://github.com/user-attachments/assets/4ebc71ba-0fd5-4bc5-8104-257d3a9c3e6f" />



## Result:
  The program is executed successfully

