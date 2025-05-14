#include <stdio.h>
#define SIZE 100

// Function to insert an element
int insert(int arr[], int *n, int value) {
    if (*n < SIZE) {
        arr[*n] = value;
        (*n)++;
        return 1;
    }
    return 0;
}

// Function to display array
void display(int arr[], int n) {
    if (n == 0) {
        printf("Array is empty.\n");
        return;
    }
    printf("Array elements: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Function to find an element
int find(int arr[], int n, int value) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == value) return i;
    }
    return -1;
}

// Function to delete an element
int delete(int arr[], int *n, int value) {
    for (int i = 0; i < *n; i++) {
        if (arr[i] == value) {
            for (int j = i; j < *n - 1; j++) {
                arr[j] = arr[j + 1];
            }
            (*n)--;
            return 1;
        }
    }
    return 0;
}

// Function to find smallest number
int findSmallest(int arr[], int n) {
    if (n == 0) return -1;
    int min = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] < min) min = arr[i];
    }
    return min;
}

// Function to find largest number
int findLargest(int arr[], int n) {
    if (n == 0) return -1;
    int max = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}

// Function to reverse the array
void reverse(int arr[], int n) {
    int temp;
    for (int i = 0; i < n / 2; i++) {
        temp = arr[i];
        arr[i] = arr[n - 1 - i];
        arr[n - 1 - i] = temp;
    }
    printf("Array reversed.\n");
}

// Function to find duplicate numbers
void findDuplicates(int arr[], int n) {
    int found = 0;
    printf("Duplicate numbers: ");
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] == arr[j]) {
                int alreadyPrinted = 0;
                for (int k = 0; k < i; k++) {
                    if (arr[k] == arr[i]) {
                        alreadyPrinted = 1;
                        break;
                    }
                }
                if (!alreadyPrinted) {
                    printf("%d ", arr[i]);
                    found = 1;
                }
                break;
            }
        }
    }
    if (!found) printf("None");
    printf("\n");
}

// Function to find unique numbers (appear only once)
void findUniques(int arr[], int n) {
    printf("Unique numbers: ");
    for (int i = 0; i < n; i++) {
        int count = 0;
        for (int j = 0; j < n; j++) {
            if (arr[i] == arr[j]) count++;
        }
        if (count == 1) {
            printf("%d ", arr[i]);
        }
    }
    printf("\n");
}

int main() {
    int arr[SIZE], n = 0, choice, val, result;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Insert\n2. Display\n3. Find\n4. Delete\n5. Smallest\n6. Largest\n");
        printf("7. Reverse\n8. Duplicates\n9. Unique numbers\n10. Different numbers\n0. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            printf("Enter value to insert: ");
            scanf("%d", &val);
            result = insert(arr, &n, val);
            if (result) printf("Inserted successfully.\n");
            else printf("Array is full.\n");
            break;

        case 2:
            display(arr, n);
            break;

        case 3:
            printf("Enter value to find: ");
            scanf("%d", &val);
            result = find(arr, n, val);
            if (result != -1) printf("Found at index %d\n", result);
            else printf("Not found.\n");
            break;

        case 4:
            printf("Enter value to delete: ");
            scanf("%d", &val);
            result = delete(arr, &n, val);
            if (result) printf("Deleted successfully.\n");
            else printf("Not found.\n");
            break;

        case 5:
            result = findSmallest(arr, n);
            if (result != -1) printf("Smallest number: %d\n", result);
            else printf("Array is empty.\n");
            break;

        case 6:
            result = findLargest(arr, n);
            if (result != -1) printf("Largest number: %d\n", result);
            else printf("Array is empty.\n");
            break;

        case 7:
            reverse(arr, n);
            break;

        case 8:
            findDuplicates(arr, n);
            break;

        case 9:
            findUniques(arr, n);
            break;

        case 10:
            findUniques(arr, n); // Same as case 9 for different numbers
            break;

        case 0:
            return 0;

        default:
            printf("Invalid choice.\n");
        }
    }
}
