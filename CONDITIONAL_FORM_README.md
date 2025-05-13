# Conditional Form Fields for ActionKit

This feature allows you to display petition form fields conditionally based on user data:

1. Users with phone number and SMS opt-in: Show minimal fields (email & zip)
2. Users with phone number but no SMS opt-in: Show email, zip, and opt-in checkbox
3. Users with no phone number: Show email, zip, phone field, and opt-in checkbox

## Implementation Details

The solution directly modifies the main `user_form.html` template to include conditional logic. This means:

1. The conditional form will be used by ALL petition pages in the templateset
2. No additional configuration is needed on individual pages
3. The existing ActionKit form flow remains unchanged

## How to Test

### Testing with Preview Mode

1. In the ActionKit admin, go to the Templates section
2. Select a petition page to preview
3. Make sure this templateset is selected
4. Click Preview

You can test different user scenarios:
- Log out to see the experience for users with no data
- Log in with different user accounts to test various scenarios

## Technical Implementation

The solution uses three methods to handle conditional fields:

1. **Server-side templating** determines initial field visibility based on user data
2. **Hidden fields** track user data like SMS opt-in status
3. **Client-side JavaScript** handles dynamic updates when users are recognized or log out

### SMS Opt-In Field

The SMS opt-in checkbox is a custom field that:
- Appears when users don't already have opt-in status
- Includes a styled disclaimer
- Saves to the custom user field `sms_opt_in` when checked

## Deployment Instructions

1. Upload this templateset or make the changes to the existing templateset
2. Test the changes using preview mode
3. Apply the templateset to your petition pages

## Configuration Options

You may want to customize:
- The opt-in checkbox text and disclaimer
- The styling of the opt-in checkbox
- Which fields are conditionally shown/hidden

Make these changes in the `user_form.html` file.