# Date Booking Management Project 😊

![Your Logo](./assets/img/1716296373896.jpg)

---

## Description

This project was created as part of my web development training. It allows you to calculate the duration of a booking based on the start and end dates selected by the user. The total price of the booking is automatically calculated based on the number of days. 📅💰

## Features 🌟

- **Date Selection:**
  - The start date is automatically set to the current date. 🗓️
  - The end date is automatically set to the day after the current date. 🕒
  - The user can adjust these dates, and the end date cannot be earlier than the start date, and vice versa. ⏳

- **Total Price Calculation:**
  - The total price is calculated based on the number of days between the start and end dates. 💸
  - The price is based on a per-night rate, displayed in the `nightPrice` element. 🏷️

## Code Description 📝

The JavaScript code implements the following features:

1. **Date Initialization:**
   - The current date is set as the minimum date for the start date input (`start_date`). ✅
   - Tomorrow's date is set as the minimum date for the end date input (`end_date`). ⏩

2. **Event Listeners:**
   - An event is added to the start date to adjust the end date if it's earlier than the start date. 🔄
   - An event is added to the end date to adjust the start date if it's later than the end date. 🔄

3. **Price Calculation:**
   - Whenever a date is changed, the number of days between the start and end date is calculated. 📊
   - The total price is calculated by multiplying the number of days by the per-night rate (`nightPrice`). 💵

## Code

```javascript
// Convert today date to input format
const today = new Date().toISOString().split("T")[0];
start_date.value = today;
start_date.min = today;

// Tomorrow date calc
let tomorrow = new Date();
tomorrow.setDate(tomorrow.getDate() + 1);

// Convert to input format
let tomorrowFormat = tomorrow.toISOString().split("T")[0];
end_date.value = tomorrowFormat;
end_date.min = tomorrowFormat;

start_date.addEventListener("change", (e) => {
  let day = new Date(e.target.value);

  if (end_date.value < start_date.value) {
    day.setDate(day.getDate() + 1);
    end_date.value = day.toISOString().split("T")[0];
  }
});

end_date.addEventListener("change", (e) => {
  let day = new Date(e.target.value);

  if (end_date.value < start_date.value) {
    day.setDate(day.getDate() - 1);
    start_date.max = day.toISOString().split("T")[0];
  }
})

const bookingCalc = () => {
  let diffTime = Math.abs(new Date(end_date.value) - new Date(start_date.value));
  let diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
  
  total.textContent = diffDays * nightPrice.textContent;
}

start_date.addEventListener("change", bookingCalc);
end_date.addEventListener("change", bookingCalc);

bookingCalc();
```

## Authors 👨‍💻

This project was created as part of my web development training. It was not originally created by me but is based on a learning project to understand date handling and events in JavaScript. 🎓
