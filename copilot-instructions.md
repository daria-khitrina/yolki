# Best Practices for HTML Email Design

This document outlines the best practices for creating HTML emails, ensuring compatibility and consistent rendering across email clients.

---

## 1. Use of Tables for Layout
- **Why**: Tables ensure consistent rendering across email clients.
- **How**: Use `<table>` with `role="presentation"` for layout purposes.
  ```html
  <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
  ```

---

## 2. Inline CSS
- **Why**: Many email clients strip out `<style>` tags.
- **How**: Apply styles inline for critical design elements.
  ```html
  <td align="center" style="padding: 40px 12px;">
  ```

---

## 3. Conditional Comments for Outlook
- **Why**: Outlook uses the Word rendering engine, requiring specific handling.
- **How**: Use conditional comments to target Outlook-specific styles.
  ```html
  <!--[if mso]>
  <style type="text/css">
      table {border-collapse: collapse;}
  </style>
  <![endif]-->
  ```

---

## 4. Responsive Design with Max Width
- **Why**: Ensures the email looks good on both desktop and mobile devices.
- **How**: Use `max-width` and `margin: 0 auto` to center and constrain content.
  ```html
  <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="max-width: 600px; margin: 0 auto;">
  ```

---

## 5. Fallback Fonts
- **Why**: Not all email clients support custom fonts.
- **How**: Include a stack of fallback fonts.
  ```html
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
  ```

---

## 6. Alt Text for Images
- **Why**: Provides context if images fail to load.
- **How**: Always include descriptive `alt` attributes for images.
  ```html
  <img src="https://example.com/logo.png" alt="Logo" width="237" height="27" style="display: block;">
  ```

---

## 7. Clickable Links with Clear Call-to-Actions
- **Why**: Improves user engagement and accessibility.
- **How**: Use clear, actionable text for links and buttons.
  ```html
  <a href="#" style="display: inline-block; font-size: 16px; line-height: 1.2; font-weight: 600; color: #0D0B0A; text-decoration: none; white-space: nowrap;">Click Here</a>
  ```

---

## 8. Background Images with Fallbacks
- **Why**: Background images are not supported in all email clients.
- **How**: Use a solid background color as a fallback.
  ```html
  background: linear-gradient(to bottom, rgba(13,11,10,0) 40%, rgba(13,11,10,0.5) 100%), url('https://example.com/image.png') center center / cover no-repeat;
  ```

---

## 9. VML for Outlook Backgrounds
- **Why**: Ensures background images render in Outlook.
- **How**: Use VML for background images in Outlook.
  ```html
  <!--[if mso]>
  <v:rect xmlns:v="urn:schemas-microsoft-com:vml" fill="true" stroke="false" style="width:600px; height:363px;">
      <v:fill type="frame" src="https://example.com/image.png" />
      <v:textbox inset="16px,32px,16px,32px">
  <![endif]-->
  ```

---

## 10. Mobile-Friendly Design
- **Why**: Many users open emails on mobile devices.
- **How**: Use `min-height` for blocks and `padding` for touch-friendly buttons.

---

## 11. Unsubscribe Link
- **Why**: Compliance with email marketing laws (e.g., GDPR, CAN-SPAM).
- **How**: Always include a visible unsubscribe link.
  ```html
  <a href="%unsubscribe-link%" style="color: #977444; text-decoration: none;">Unsubscribe</a>
  ```

---

## 12. Web-Safe Colors
- **Why**: Ensures consistent rendering across devices.
- **How**: Use hex codes for colors.
  ```html
  color: #e3dfd3;
  ```

---

## 13. Avoid External JavaScript or Complex CSS
- **Why**: Many email clients block JavaScript and advanced CSS features.
- **How**: Stick to simple, inline CSS and avoid JavaScript.

---

## 14. Testing for Dark Mode
- **Why**: Many users enable dark mode on their devices.
- **How**: Explicitly define text and background colors to prevent unwanted changes in dark mode.

---

## 15. Fallback Links for Social Media
- **Why**: Ensures users can access social media even if icons fail to load.
- **How**: Provide alternative text and links for social media icons.
  ```html
  <a href="https://www.instagram.com/example/" style="display: inline-block;">
      <img src="https://example.com/instagram-icon.png" alt="Instagram" width="24" height="24" style="display: block;">
  </a>
  ```

---

## 16. Inline Font-Family Styles
- **Why**: Some email clients, like Gmail, may ignore global styles. Inlining the `font-family` ensures consistent rendering across all clients.
- **How**: Apply the `font-family` inline to all text elements.
  ```html
  <h1 style="font-family: 'Tilda Sans VF', sans-serif;">Header Text</h1>
  <p style="font-family: 'Tilda Sans VF', sans-serif;">Paragraph Text</p>
  <a href="#" style="font-family: 'Tilda Sans VF', sans-serif;">Link Text</a>
  ```