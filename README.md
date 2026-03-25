# Subtask-2
Add your full C++ program here 
 
 #include <iostream>
#include <string>
#include <cmath>
#include <algorithm>

using namespace std; 

// Function to convert decimal to binary 
string decimalToBinary(int decimal) { 
    if (decimal == 0) return "0"; // Special case for decimal 0 
    
    string binary = ""; // Initialize empty string to store binary representation
    
    while (decimal > 0) {
        binary = to_string(decimal % 2) + binary; // Append remainder to binary string
        decimal /= 2; // Divide decimal number by 2
    }
    
    return binary;
}

// Function to convert binary to decimal
int binaryToDecimal(string binary) {
    int decimal = 0;
    int power = 0;
    
    // Iterate over each digit of binary number from right to left
    for (int i = binary.length() - 1; i >= 0; i--) {
        if (binary[i] == '1') {
            decimal += pow(2, power); // Add 2^power to decimal if digit is '1'
        }
        power++; // Increment power for next position
    }
    
    return decimal;
}

// Function to convert decimal to hexadecimal
string decimalToHexadecimal(int decimal) {
    if (decimal == 0) return "0"; // Special case for decimal 0
    
    string hex = ""; // Initialize empty string to store hexadecimal representation
    char hexDigits[] = "0123456789ABCDEF"; // Hexadecimal digits
    
    while (decimal > 0) {
        hex = hexDigits[decimal % 16] + hex; // Get the corresponding hex digit and append to hex string
        decimal /= 16; // Divide decimal number by 16
    }
    
    return hex;
}

// Function to convert hexadecimal to decimal
int hexadecimalToDecimal(string hex) {
    int decimal = 0;
    int power = 0;
    
    // Iterate over each digit of hexadecimal number from right to left
    for (int i = hex.length() - 1; i >= 0; i--) {
        char digit = hex[i];
        int value;
        
        // Convert hexadecimal digit to its corresponding decimal value
        if (digit >= '0' && digit <= '9') {
            value = digit - '0';
        } else if (digit >= 'A' && digit <= 'F') {
            value = 10 + (digit - 'A');
        } else if (digit >= 'a' && digit <= 'f') {
            value = 10 + (digit - 'a');
        } else {
            value = 0; // In case of invalid hex digit
        }
        
        decimal += value * pow(16, power); // Add value * 16^power to decimal
        power++; // Increment power for next position
    }
    
    return decimal;
}

int main() {
    int choice;
    cout << "Conversion Menu:\n";
    cout << "1. Decimal to Binary\n";
    cout << "2. Binary to Decimal\n";
    cout << "3. Decimal to Hexadecimal\n";
    cout << "4. Hexadecimal to Decimal\n";
    cout << "Enter your choice (1, 2, 3, or 4): ";
    cin >> choice;
    
    if (choice == 1) {
        int decimal;
        cout << "Enter a decimal number: ";
        cin >> decimal;
        string binary = decimalToBinary(decimal);
        cout << "Binary representation: " << binary << endl;
    } else if (choice == 2) {
        string binary;
        cout << "Enter a binary number: ";
        cin >> binary;
        int decimal = binaryToDecimal(binary);
        cout << "Decimal representation: " << decimal << endl;
    } else if (choice == 3) {
        int decimal;
        cout << "Enter a decimal number: ";
        cin >> decimal;
        string hex = decimalToHexadecimal(decimal);
        cout << "Hexadecimal representation: " << hex << endl;
    } else if (choice == 4) {
        string hex;
        cout << "Enter a hexadecimal number: ";
        cin >> hex;
        int decimal = hexadecimalToDecimal(hex);
        cout << "Decimal representation: " << decimal << endl;
    } else {
        cout << "Invalid choice. Please enter 1, 2, 3, or 4." << endl;
    }
    
    return 0;
}
 
 
 
 
 


