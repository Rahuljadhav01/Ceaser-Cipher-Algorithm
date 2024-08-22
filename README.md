# Ceaser-Cipher-Algorithm
Implementation of the Caesar Cipher Algorithm as part of my internship task.
Code -
def encrypt(message, shift):
   encrypted_message = ""
   for char in message:
      if char.isalpha():
         shift_amount = shift % 26
         start = ord('A') if char.isupper() else ord('a')
         new_char = chr(start + (ord(char) - start + shift_amount) % 26)
         encrypted_message += new_char
      else:
         encrypted_message += char
   return encrypted_message

def decrypt(message, shift):
   return encrypt(message, -shift)

def main():
   print("Caesar Cipher Encryption and Decryption")

   while True:
      choice = input("Do you want yo (E)ncrypt or (D)ecrypt? (E/D):").strip().upper()
      if choice in ['E','D']:
         message = input("Enter your message: ")
         shift = int(input("Enter the shift value: "))

         if choice == 'E':
            encrypted_message = encrypt(message, shift)
            print(f"Encrypted message: {encrypted_message}")
            
         elif choice =='D':
            decrypted_message = decrypt(message, shift)
            print(f"Decrypted message: {decrypted_message}")

         another = input("Do you want to perform another operation? (Y/N): ").strip().upper()
         if another != 'Y':
            break
         else:
            print("Invalid choice. Please selet 'E' to encrypt or 'D' to decrypt.")

if __name__ == "__name__":
   main()
