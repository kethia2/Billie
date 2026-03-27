#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_TRIES 7
#define MIN_NUM   1
#define MAX_NUM   100

void print_banner() {
    printf("╔══════════════════════════════════╗\n");
    printf("║      NUMBER GUESSING GAME        ║\n");
    printf("║   Guess a number from 1 to 100   ║\n");
    printf("╚══════════════════════════════════╝\n\n");
}

void print_result(int won, int secret, int tries) {
    if (won) {
        printf("\n🎉 Correct! You guessed it in %d %s!\n",
               tries, tries == 1 ? "try" : "tries");
    } else {
        printf("\n💀 Out of tries! The number was %d.\n", secret);
    }
}

int main() {
    srand((unsigned int)time(NULL));

    int secret = (rand() % MAX_NUM) + MIN_NUM;
    int guess   = 0;
    int tries   = 0;
    int won     = 0;

    print_banner();
    printf("You have %d tries. Good luck!\n\n", MAX_TRIES);

    while (tries < MAX_TRIES) {
        printf("Try %d/%d — Enter your guess: ", tries + 1, MAX_TRIES);

        if (scanf("%d", &guess) != 1) {
            printf("Invalid input. Please enter a number.\n");
            while (getchar() != '\n'); // clear input buffer
            continue;
        }

        tries++;

        if (guess < MIN_NUM || guess > MAX_NUM) {
            printf("Please guess between %d and %d.\n\n", MIN_NUM, MAX_NUM);
            tries--; // don't count invalid range as a try
            continue;
        }

        if (guess < secret) {
            printf("📈 Too low!\n\n");
        } else if (guess > secret) {
            printf("📉 Too high!\n\n");
        } else {
            won = 1;
            break;
        }
    }

    print_result(won, secret, tries);

    return 0;
}
