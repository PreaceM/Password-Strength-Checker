
<div align="center">
  <h1>🔐 Password Strength Checker</h1>
  <p> 
    
## Objective

This Python Password Strength Checker evaluates passwords against security standards, checking length, complexity, and common patterns. It provides instant feedback to help users create stronger passwords through actionable improvement suggestions.

## Skills Learned

- Python programming (functions, conditionals, loops)
- Input/output handling (CLI interaction)
  
## Tools Used

- Python
- Visual Studio Code </p>
</div>

<div style="background: #f8f9fa; border-radius: 8px; padding: 20px; border: 1px solid #e1e4e8; font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace; font-size: 14px; line-height: 1.5; overflow-x: auto;">
  
<pre><code>import re


def check_password_strength(password):
    """Check the strength of a password and provide feedback."""
    
    # Initialize variables
    strength = 0
    feedback = []
    
    # Length check
    if len(password) < 8:
        feedback.append("Password is too short (minimum 8 characters)")
    else:
        strength += 1
        if len(password) >= 12:
            strength += 1
    
    # Uppercase letters check
    if re.search(r'[A-Z]', password):
        strength += 1
    else:
        feedback.append("Add uppercase letters")
    
    # Lowercase letters check
    if re.search(r'[a-z]', password):
        strength += 1
    else:
        feedback.append("Add lowercase letters")
    
    # Numbers check
    if re.search(r'[0-9]', password):
        strength += 1
    else:
        feedback.append("Add numbers")
    
    # Special characters check
    if re.search(r'[^A-Za-z0-9]', password):
        strength += 1
    else:
        feedback.append("Add special characters (e.g., !@#$%^&*)")
    
    # Common password check (very basic version)
    common_passwords = ['password', '123456', 'qwerty', 'letmein', 'welcome']
    if password.lower() in common_passwords:
        strength = 0
        feedback.append("This is a very common password - choose something more unique")
    
    # Determine strength level
    if strength == 0:
        strength_text = "Very Weak"
    elif strength <= 2:
        strength_text = "Weak"
    elif strength <= 4:
        strength_text = "Moderate"
    elif strength <= 6:
        strength_text = "Strong"
    else:
        strength_text = "Very Strong"
    
    # Check for consecutive characters
    if re.search(r'(.)\1{2,}', password):
        feedback.append("Avoid repeating the same character multiple times in a row")
        strength = max(0, strength - 1)
    
    # Check for sequences (e.g., "1234", "abcd")
    if (re.search(r'123|234|345|456|567|678|789|890', password) or
        re.search(r'abc|bcd|cde|def|efg|fgh|ghi|hij|ijk|jkl|klm|lmn|mno|nop|opq|pqr|qrs|rst|stu|tuv|uvw|vwx|wxy|xyz', password.lower())):
        feedback.append("Avoid simple sequences of letters or numbers")
        strength = max(0, strength - 1)
    
    return strength_text, feedback


def main():
    print("Password Strength Checker")
    print("-------------------------")
    
    while True:
        password = input("Enter a password to check (or 'quit' to exit): ")
        
        if password.lower() == 'quit':
            break
            
        strength, feedback = check_password_strength(password)
        
        print(f"\nPassword Strength: {strength}")
        if feedback:
            print("Suggestions to improve:")
            for item in feedback:
                print(f"- {item}")
        else:
            print("Your password is strong! No suggestions for improvement.")
        
        print()


if __name__ == "__main__":
    main()</code></pre>
</div>

<div style="margin-top: 20px; background: #f6f8fa; padding: 15px; border-radius: 6px; border-left: 4px solid #0366d6;">
  <h3 style="margin-top: 0;">✨ Features</h3>
  <ul style="padding-left: 20px;">
    <li>8+ security checks for comprehensive evaluation</li>
    <li>Detailed feedback for password improvement</li>
    <li>Common password detection</li>
    <li>Pattern recognition (sequences, repeating chars)</li>
  </ul>
</div>
