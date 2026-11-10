# joseph_workshop_energy_cost_estimator-
"""
Workshop Energy Cost Estimator
-------------------------------
Enter each machine's name, power (watts) and daily hours of use.
The program works out daily and monthly energy in kWh and the cost
at your local electricity tariff (in Naira per kWh).

My own twist: an "Energy Hog Ranking" with a text bar chart, plus a
"What if?" saver that shows how much money you keep if you cut the
biggest consumer's running time. The report can also be saved to a file.
"""

# ---------- Tariff presets (Naira per kWh) ----------
# These are approximate and DisCo rates change, so always check your own bill.
TARIFF_NAMES = ["Band A (about 24 hrs supply)", "Band B (about 16 hrs supply)",
                "Band C (about 12 hrs supply)", "Band D (about 8 hrs supply)"]
TARIFF_RATES = [209.50, 63.30, 50.00, 32.00]


def get_number(prompt, minimum, maximum, whole_number=False):
    """Keep asking until the user types a valid number in the range.
    Returns the number as an int or a float."""
    while True:
        text = input(prompt).strip()
        try:
            # Convert the typed text into a number (int() or float())
            value = int(text) if whole_number else float(text)
        except ValueError:
            print("  That is not a valid number. Please type digits only, e.g. 5 or 2.5.")
            continue
        if value < minimum or value > maximum:
            print(f"  Please enter a value between {minimum} and {maximum}.")