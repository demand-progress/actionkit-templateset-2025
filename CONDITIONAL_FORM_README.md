# Conditional Form Fields for ActionKit

This feature allows you to display petition form fields conditionally based on user data:

1. Users with phone number and SMS opt-in: Show only standard ActionKit "Not X? Click here" message
2. Users with phone number but no SMS opt-in: Show opt-in checkbox
3. Users with no phone number: Show phone field and opt-in checkbox
4. Unknown users: Show standard form with all fields

## Implementation Details

The solution uses a custom user form wrapper (`conditional_user_form_wrapper.html`) that:

1. For recognized users with missing data, shows only the specific fields they need to complete
2. For recognized users with all data, shows just the standard logout message
3. For unknown users, includes the regular form

## How to Test

### Testing with Preview Mode

1. In the ActionKit admin, go to the Templates section
2. Select a petition page to preview
3. Make sure this templateset is selected
4. Click Preview

Testing different scenarios:
- Log out to see the experience for users with no data (full form)
- Log in with different user accounts to test various scenarios:
  - User with phone + opt-in: Just shows "Not X? Click here" 
  - User with phone but no opt-in: Shows opt-in checkbox
  - User with no phone: Shows phone field and opt-in checkbox

## Technical Implementation

The solution uses these technical approaches:

1. **Server-side templating** determines which fields to show based on user data
2. **ActionKit field rendering** uses the CMS-configured field labels and properties
3. **Styled display** shows the extra fields nicely to recognized users

## Configuration Options

You may want to customize:
- The message shown to recognized users missing data
- The styling of the extra fields container
- The opt-in checkbox text and disclaimer

Make these changes in the `conditional_user_form_wrapper.html` file.