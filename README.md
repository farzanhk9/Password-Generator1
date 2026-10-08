import secrets2
import string


def generate_password(length=16, use_symbols=True):
    characters = string.ascii_letters + string.digits

    if use_symbols:
        characters += string.punctuation

    password = ''.join(
        secrets.choice(characters)
        for _ in range(length)
    )

    return password


def main():
    print("🔐 Secure Password Generator")
    print("-" * 35)

    try:
        length = int(input("Password length: "))

        if length < 8:
            print("❌ Password should be at least 8 characters.")
            return

        symbols = input("Include symbols? (y/n): ").lower() == "y"

        password = generate_password(length, symbols)

        print("\n✅ Your secure password:")
        print(password)

    except ValueError:
        print("❌ Please enter a valid number.")


if __name__ == "__main__":
    main()
