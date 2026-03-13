#include <stdio.h>
#include <string.h>

struct Contact {
    char name[50];
    char phone[15];
    char email[50];
};

int main() {
    struct Contact contacts[100];
    int count = 0, i, choice;
    char searchName[50];

    while (1) {
        printf("\n--- Contact Book ---\n");
        printf("1. Add Contact\n");
        printf("2. Display Contacts\n");
        printf("3. Search Contact\n");
        printf("4. Delete Contact\n");
        printf("5. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar(); // clear input buffer

        switch (choice) {

        case 1:
            printf("Enter name: ");
            gets(contacts[count].name);

            printf("Enter phone: ");
            gets(contacts[count].phone);

            printf("Enter email: ");
            gets(contacts[count].email);

            count++;
            printf("Contact added successfully!\n");
            break;

        case 2:
            printf("\n--- Contact List ---\n");
            for (i = 0; i < count; i++) {
                printf("%d. %s | %s | %s\n",
                       i + 1,
                       contacts[i].name,
                       contacts[i].phone,
                       contacts[i].email);
            }
            break;

        case 3:
            printf("Enter name to search: ");
            gets(searchName);

            for (i = 0; i < count; i++) {
                if (strcmp(searchName, contacts[i].name) == 0) {
                    printf("Contact Found: %s | %s | %s\n",
                           contacts[i].name,
                           contacts[i].phone,
                           contacts[i].email);
                    break;
                }
            }

            if (i == count)
                printf("Contact not found!\n");
            break;

        case 4:
            printf("Enter name to delete: ");
            gets(searchName);

            for (i = 0; i < count; i++) {
                if (strcmp(searchName, contacts[i].name) == 0) {

                    for (int j = i; j < count - 1; j++) {
                        contacts[j] = contacts[j + 1];
                    }

                    count--;
                    printf("Contact deleted successfully!\n");
                    break;
                }
            }

            if (i == count)
                printf("Contact not found!\n");
            break;

        case 5:
            printf("Exiting program...\n");
            return 0;

        default:
            printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
}