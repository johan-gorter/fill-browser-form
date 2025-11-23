---
name: fill-browser-form
description: Fills in a form in the user's browser with the given data.
---

## Overview

This skill is designed to assist users in automating the process of filling out web forms directly in their browsers. By following a structured approach, it enables the generation of JavaScript code that can be executed in the browser's console to populate form fields fast and accurately.

## When to Use This Skill

Use this Skill when a user needs to fill form fields in their browser

## Workflow

### Step 1: Extract HTML from the page

When the user asks to fill a form, you respond immediately with these instructions to obtain the HTML of the page:
Ask the user to open DevTools (F12) in their browser and run the following command in the console to copy the page HTML to their clipboard:

```javascript
{
  const textarea = document.createElement("textarea");
  textarea.value = document.body.outerHTML;
  document.body.appendChild(textarea);
  textarea.select();
  document.execCommand("copy");
  document.body.removeChild(textarea);
  ("pagina gekopieerd naar klembord");
}
```

Just show this code snippet in a code block inline, do not use an artifact for this step.

Ask the user to paste the result back to you.

### Step 2: Analyze the HTML Structure

When the user provides the HTML, analyze the form fields in the HTML and understand:

- How fields are labeled and structured
- How to add new rows/sections/instances if needed
- The DOM structure how to navigate from a label to the accompanying input element

### Step 3: Generate the Form-Filling Script

Create a script that follows these important rules:

#### Timing Requirements

- Wait **200ms** between filling different fields
- Wait **500ms** after actions that modify the page (e.g., adding new rows/sections/fields, opening/closing panels)

#### Field Filling Process

For each field, perform these actions:

1. Focus the field (this scrolls it into view)
2. Set the `value` or `checked` attribute
3. Fire a synthetic `change` or `input` event

#### Element Selection Strategy

Always find the correct element using this approach:

- Search for the element based on its associated text label
- Take the last element on the page with that text label
- Navigate to the appropriate ancestor element
- Use `querySelector` from there to find the correct input element
- Use helper functions specific to the HTML structure

#### Helper Function Examples

```javascript
// Finds the last input element with an associated label element on the page
function findInputElementByLabel(labelText) {
  const labels = Array.from(document.querySelectorAll("label"));
  const matchingLabel = labels.findLast((label) =>
    label.textContent.includes(labelText)
  );

  if (matchingLabel) {
    if (matchingLabel.htmlFor) {
      return document.getElementById(matchingLabel.htmlFor);
    }
    const nestedInput = matchingLabel.querySelector("input,select,textarea");
    if (nestedInput) {
      return nestedInput;
    }
  }
  throw new Error("Field not found for label: " + labelText);
}

// Finds the input element associated with the last <div class="label"> containing labelText
function findInputElementByDivLabel(labelText) {
  const label = Array.from(document.querySelectorAll("div.label")).findLast(
    (el) => el.textContent.includes(labelText)
  );

  if (!label) {
    throw new Error("Label not found: " + labelText);
  }

  // Navigate to the container parent
  const fieldContainer = label.closest("div.container");

  const input = fieldContainer.querySelector("custom-text-input input");
  if (!input) {
    throw new Error("Input not found for label: " + labelText);
  }

  return input;
}
```

### Step 4: Script Format

Create a simple, compact script with:

- Each declaration and function documented with one line of comment in language the user uses.
- Wrapped in an IIFE (Immediately Invoked Function Expression)
- Proper error handling and logging to the console

### Step 5: Delivery Instructions

Provide the script as an artifact and instruct the user to:

1. Run the script in the DevTools console
2. If something goes wrong, respond with the console output or a description of what failed
