#include <stdio.h>
#include <string.h>

#define MAX_PRODUCTS 100

// Structure to store product details
struct Product {
    char name[50];
    int quantity;
    float price;
    float total_price;
};

// Function to calculate total bill amount
float calculate_total(struct Product products[], int num_products) {
    float total = 0;
    for (int i = 0; i < num_products; i++) {
        products[i].total_price = products[i].quantity * products[i].price;
        total += products[i].total_price;
    }
    return total;
}

// Function to apply discount
float apply_discount(float total) {
    float discount = 0;
    
    // Applying discount based on total amount
    if (total > 1000 && total <= 2000) {
        discount = total * 0.05;  // 5% discount for totals between 1000 and 2000
    } else if (total > 2000) {
        discount = total * 0.10;  // 10% discount for totals above 2000
    }
    
    return discount;
}

// Function to generate the bill
void generate_bill(struct Product products[], int num_products, float total, float discount) {
    printf("\n--- Shopping Mall Bill ---\n");
    printf("Product Name\tQuantity\tPrice\tTotal Price\n");
    printf("----------------------------------------------------\n");
    
    for (int i = 0; i < num_products; i++) {
        printf("%-15s\t%d\t\t%.2f\t%.2f\n", products[i].name, products[i].quantity, products[i].price, products[i].total_price);
    }
    
    printf("----------------------------------------------------\n");
    printf("Total: $%.2f\n", total);
    if (discount > 0) {
        printf("Discount: -$%.2f\n", discount);
    }
    printf("Final Amount: $%.2f\n", total - discount);
    printf("----------------------------------------------------\n");
}

int main() {
    struct Product products[MAX_PRODUCTS];
    int num_products;
    float total, discount;

    // Step 1: Input the number of products
    printf("Enter the number of products: ");
    scanf("%d", &num_products);

    // Validation for number of products
    if (num_products < 0) {
        printf("Error: Number of products cannot be negative.\n");
        return 1; // Exit the program with an error code
    }

    // Step 2: Accept details of each product
    for (int i = 0; i < num_products; i++) {
        printf("\n--- Enter details for product %d ---\n", i + 1);
        
        printf("Product Name: ");
        scanf("%s", products[i].name);
        
        // Input quantity with validation
        do {
            printf("Quantity : ");
            scanf("%d", &products[i].quantity);
            if (products[i].quantity < 0) {
                printf("Error: Quantity cannot be negative. Please try again.\n");
            }
        } while (products[i].quantity < 0);

        // Input price with validation
        do {
            printf("Price per unit : ");
            scanf("%f", &products[i].price);
            if (products[i].price < 0) {
                printf("Error: Price cannot be negative. Please try again.\n");
            }
        } while (products[i].price < 0);
    }

    // Step 3: Calculate the total bill amount
    total = calculate_total(products, num_products);

    // Step 4: Apply discount if eligible
    discount = apply_discount(total);

    // Step 5: Generate the final bill
    generate_bill(products, num_products, total, discount);

    return 0;
}
