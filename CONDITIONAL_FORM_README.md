# Conditional Form Fields for ActionKit

This feature allows you to display petition form fields conditionally based on user data:

1. Users with phone number and SMS opt-in: Show minimal fields (email & zip)
2. Users with phone number but no SMS opt-in: Show email, zip, and opt-in checkbox
3. Users with no phone number: Show email, zip, phone field, and opt-in checkbox

## Files Added

- `conditional_user_form.html`: The form template with conditional logic
- `conditional_user_form_wrapper.html`: Wrapper template that includes the conditional form
- `conditional_petition.html`: A petition page template that uses the conditional form

## How to Use

### Testing with Preview Mode

1. In the ActionKit admin, go to the Templates section
2. Select a petition page to preview
3. Enter "conditional_petition.html" in the Template field
4. Click Preview

You can test different user scenarios:
- Log out to see the experience for users with no data
- Log in with different user accounts to test various scenarios

### Deploying to Production

After testing in preview mode:

1. Create a petition page in ActionKit
2. Set the template to "conditional_petition.html"
3. Set the required fields (typically email and zip)
4. Publish your page

### Implementation Details

The solution uses three methods to handle conditional fields:

1. **Server-side templating** determines initial field visibility based on user data
2. **Hidden fields** track user data like SMS opt-in status
3. **Client-side JavaScript** handles dynamic updates when users are recognized or log out

## SMS Opt-In Field

The SMS opt-in checkbox is a custom field that:
- Appears when users don't already have opt-in status
- Includes a styled disclaimer
- Saves to the custom user field `sms_opt_in` when checked

## Maintaining This Feature

If you need to modify this feature:

1. Edit the files using the ActionKit admin or upload a new templateset
2. Always test changes using preview mode before deploying
3. Test with different user scenarios to ensure all paths work correctly

For questions or issues, contact your ActionKit administrator.