
import re
from collections import Counter
from pathlib import Path

def analyze_text(filename):
    path = Path(filename)

    if not path.exists():
        print("File not found!")
        return

    text = path.read_text(encoding="utf-8").lower()

    words = re.findall(r"\b[a-zA-Z0-9]+\b", text)
    counter = Counter(words)

    print(f"\nTotal words: {len(words)}")
    print(f"Unique words: {len(counter)}")

    print("\nTop 10 frequent words:")

    for word, count in counter.most_common(10):
        print(f"{word}: {count}")

def main():
    filename = input("Enter text file path: ")
    analyze_text(filename)

if __name__ == "__main__":
    main()
