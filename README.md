# 12-vs-24-Hours
def convertTime(time_str):
    # Check if input is in 12-hour format
    if "am" in time_str.lower() or "pm" in time_str.lower():
        # Convert 12-hour to 24-hour format
        time, period = time_str.split(" ")
        hours, minutes = map(int, time.split(":"))
        if period.lower() == "am":
            hours = 0 if hours == 12 else hours
        elif period.lower() == "pm":
            hours = 12 if hours == 12 else hours + 12
        return f"{hours}:{minutes:02d}"
    else:
        # Convert 24-hour to 12-hour format
        hours, minutes = map(int, time_str.split(":"))
        period = "am" if hours < 12 else "pm"
        hours = hours % 12 or 12  # Convert 0 or 12 to 12 for 12-hour format
        return f"{hours}:{minutes:02d} {period}"

# Examples
print(convertTime("12:00 am"))  # Output: "0:00"
print(convertTime("6:20 pm"))  # Output: "18:20"
print(convertTime("21:00"))    # Output: "9:00 pm"
print(convertTime("5:05"))     # Output: "5:05 am"
