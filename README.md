# PRODIGY_CS_03

import re

def assess_password_strength(password):
    criteria = {
        "length": len(password) > 8,
        "uppercase": re.search(r"[A-Z]", password) is not None,
        "lowercase": re.search(r"[a-z]", password) is not None,
        "digits": re.search(r"\d", password) is not None,
        "special characters": re.search(r"[!@&*(),.?\":;'<>]", password) is not None,
    }

    strength_score = sum(criteria.values())

    if strength_score == 5:
        strength = "Very Strong"
    elif strength_score == 4:
        strength = "Strong"
    elif strength_score == 3:
        strength = "Moderate"
    elif strength_score == 2:
        strength = "Weak"
    else:
        strength = "Very Weak"

    return strength, criteria

def main():
    password = input("Enter a password to assess its strength: ")
    strength, criteria = assess_password_strength(password)

    print("\nPassword: {}".format(password))
    print("Strength: {}".format(strength))
    print("Criteria met:")
    for criterion, met in criteria.items():
        print(" {}: {}".format(criterion.replace('_', ' ').capitalize(), 'Yes' if met else 'No'))

if __name__ == "__main__":
    main()
