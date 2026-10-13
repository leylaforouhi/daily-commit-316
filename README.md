from collections import defaultdict


def summarize_expenses(expenses):
    totals = defaultdict(float)

    for category, amount in expenses:
        if amount < 0:
            raise ValueError("Expense amount cannot be negative")

        totals[category] += amount

    return dict(sorted(totals.items()))


if __name__ == "__main__":
    expenses = [
        ("Food", 12.50),
        ("Transport", 4.20),
        ("Food", 8.30),
        ("Entertainment", 15.00),
    ]

    summary = summarize_expenses(expenses)

    for category, total in summary.items():
        print(f"{category}: €{total:.2f}")

    print(f"Total spent: €{sum(summary.values()):.2f}")
