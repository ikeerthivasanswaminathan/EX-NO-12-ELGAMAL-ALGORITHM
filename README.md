# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

STEP-1: ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

STEP-2: Initialization
Select a large prime ( p ) and a primitive root ( g ) modulo ( p ) (these are public values).

STEP-3: Key Generation (Private Key)
The receiver chooses a private key ( x ) (a random integer), and computes the corresponding public key ( y = g^x mod p ).

STEP-4: Key Generation (Public Key)
The public key is ( (p, g, y) ), and the private key is ( x ).

STEP-5: Encryption and Decryption
Encryption: The sender picks a random integer ( k ), computes ( c1 = g^k mod p ), and ( c2 = m × y^k mod p ), where ( m ) is the message. The ciphertext is the pair ( (c1, c2) ).
Decryption: The receiver computes ( s = c1^x mod p ), and then calculates the plaintext message ( m = c2 × s^{-1} mod p ), where ( s^{-1} ) is the modular inverse of ( s ).

STEP-6: Security
The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:

```
#include <stdio.h>
#include <string.h>

long long power(long long a, long long b, long long p)
{
    long long r = 1;
    while (b--)
    {
        r = (r * a) % p;
    }
    return r;
}

int main()
{
    char name[20];
    long long p = 467, g = 2, x = 34, k = 3;
    printf("Enter Word: ");
    scanf("%s", name);
    long long y = power(g, x, p);
    printf("\nELGAMAL ENCRYPTION AND DECRYPTION\n\n");
    printf("Private key: %lld\n", x);
    printf("Public key : %lld\n\n", y);
    for (int i = 0; i < strlen(name); i++)
    {
        long long m = name[i];
        long long c1 = power(g, k, p);
        long long c2 = (m * power(y, k, p)) % p;
        printf("Encrypted '%c' -> (%lld, %lld)\n", (char)m, c1, c2);
        long long s = power(c1, x, p);
        long long inv = 1;
        while ((s * inv) % p != 1)
        {
            inv++;
        }
        long long d = (c2 * inv) % p;
        printf("Decrypted : %c\n\n", (char)d);
    }
    return 0;
}
```

## Output:

<img width="1916" height="895" alt="ex12op" src="https://github.com/user-attachments/assets/2d28fe20-cb54-4cd5-9f9e-af43b523391a" />

## Result:
Thus, the implementation of Elgamal Algorithm had been executed successfully.
