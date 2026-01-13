# Tax Calculator (Progressive Tax System)

status = int(input(
    "Enter filing status:\n"
    "0 = Single\n"
    "1 = Married Filing Jointly\n"
    "2 = Married Filing Separately\n"
    "3 = Head of Household\n"
))

income = float(input("Enter your taxable income: "))

tax_brackets = {
    0: [(8350, 0.10), (33950, 0.15), (82250, 0.25), (171550, 0.28), (372950, 0.33), (float('inf'), 0.35)],
    1: [(16700, 0.10), (67900, 0.15), (137050, 0.25), (208850, 0.28), (372950, 0.33), (float('inf'), 0.35)],
    2: [(8350, 0.10), (33950, 0.15), (68525, 0.25), (104425, 0.28), (186475, 0.33), (float('inf'), 0.35)],
    3: [(11950, 0.10), (45500, 0.15), (117450, 0.25), (190200, 0.28), (372950, 0.33), (float('inf'), 0.35)]
}

total_tax = 0
lower_limit = 0

for upper_limit, rate in tax_brackets[status]:
    if income > upper_limit:
        total_tax += (upper_limit - lower_limit) * rate
        lower_limit = upper_limit
    else:
        total_tax += (income - lower_limit) * rate
        break

print(f"Total tax payable: ${total_tax:.2f}")
