
# Automated Pet Feeder using Fuzzy Logic - Membership Function Plotting

This Python script implements and plots the membership functions for an automated pet feeder system using fuzzy logic. The variables involved are:

- **Hunger Level** (input)
- **Time Since Last Feeding** (input)
- **Food Dispensed** (output)

The script uses the `skfuzzy` library to define fuzzy sets and membership functions, and `matplotlib` to visualize them.

## Requirements

Ensure you have the required libraries installed:

```bash
pip install scikit-fuzzy matplotlib
```

## Code Overview

### 1. Define Universe of Discourse

Each fuzzy variable (hunger level, time since last feeding, and food dispensed) has a range, defined as the universe of discourse.

```python
x_hunger_level = np.arange(0, 11, 1)  # Hunger level range [0, 10]
x_time_since_last_feeding = np.arange(0, 11, 1)  # Time since last feeding [0, 10]
x_food_dispensed = np.arange(0, 101, 1)  # Food dispensed [0, 100] grams
```

### 2. Define Membership Functions

Membership functions define how each input/output variable maps to fuzzy sets. We use **triangular membership functions** (`fuzz.trimf`) for simplicity.

#### Hunger Level

- `low`: low hunger, fuzzy values from 0 to 5.
- `medium`: medium hunger, fuzzy values centered at 5.
- `high`: high hunger, fuzzy values from 5 to 10.

```python
hunger_level_low = fuzz.trimf(x_hunger_level, [0, 0, 5])
hunger_level_medium = fuzz.trimf(x_hunger_level, [0, 5, 10])
hunger_level_high = fuzz.trimf(x_hunger_level, [5, 10, 10])
```

#### Time Since Last Feeding

- `short`: short time since last feeding, fuzzy values from 0 to 5.
- `moderate`: moderate time since last feeding, fuzzy values centered at 5.
- `long`: long time since last feeding, fuzzy values from 5 to 10.

```python
time_since_last_feeding_short = fuzz.trimf(x_time_since_last_feeding, [0, 0, 5])
time_since_last_feeding_moderate = fuzz.trimf(x_time_since_last_feeding, [0, 5, 10])
time_since_last_feeding_long = fuzz.trimf(x_time_since_last_feeding, [5, 10, 10])
```

#### Food Dispensed

- `low`: low amount of food, fuzzy values from 0 to 50 grams.
- `medium`: medium amount of food, fuzzy values centered at 50 grams.
- `high`: high amount of food, fuzzy values from 50 to 100 grams.

```python
food_dispensed_low = fuzz.trimf(x_food_dispensed, [0, 0, 50])
food_dispensed_medium = fuzz.trimf(x_food_dispensed, [0, 50, 100])
food_dispensed_high = fuzz.trimf(x_food_dispensed, [50, 100, 100])
```

### 3. Plotting Membership Functions

We use `matplotlib` to visualize the membership functions. Each input/output variable is plotted in a separate subplot for clarity.

```python
fig, (ax0, ax1, ax2) = plt.subplots(nrows=3, figsize=(8, 8))

# Plot hunger level membership functions
ax0.plot(x_hunger_level, hunger_level_low, 'b', linewidth=1.5, label='Low')
ax0.plot(x_hunger_level, hunger_level_medium, 'g', linewidth=1.5, label='Medium')
ax0.plot(x_hunger_level, hunger_level_high, 'r', linewidth=1.5, label='High')
ax0.set_title('Hunger Level')
ax0.legend()

# Plot time since last feeding membership functions
ax1.plot(x_time_since_last_feeding, time_since_last_feeding_short, 'b', linewidth=1.5, label='Short')
ax1.plot(x_time_since_last_feeding, time_since_last_feeding_moderate, 'g', linewidth=1.5, label='Moderate')
ax1.plot(x_time_since_last_feeding, time_since_last_feeding_long, 'r', linewidth=1.5, label='Long')
ax1.set_title('Time Since Last Feeding')
ax1.legend()

# Plot food dispensed membership functions
ax2.plot(x_food_dispensed, food_dispensed_low, 'b', linewidth=1.5, label='Low')
ax2.plot(x_food_dispensed, food_dispensed_medium, 'g', linewidth=1.5, label='Medium')
ax2.plot(x_food_dispensed, food_dispensed_high, 'r', linewidth=1.5, label='High')
ax2.set_title('Food Dispensed (grams)')
ax2.legend()

# Adjust layout
plt.tight_layout()
plt.show()
```

### 4. Run the Script

Running the code will display three separate graphs showing the fuzzy membership functions for **hunger level**, **time since last feeding**, and **food dispensed**.

## Example Output

The output will show three plots representing the membership functions for each fuzzy variable.

- **Hunger Level** (Low, Medium, High)
- **Time Since Last Feeding** (Short, Moderate, Long)
- **Food Dispensed** (Low, Medium, High)

---

## Notes

- The membership functions can be customized by adjusting the triangular function parameters.
- You can add more variables or modify the fuzzy rules to better fit specific scenarios for the pet feeder.
