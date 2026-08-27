# MTU Projects — Standard Operating Procedures

Business: MTU Projects
Owner: Monty
Location: Leeds, UK
Email: info@mtuprojects.com
Phone: +44 7754 208536

---

## Website Builds

### Contact Forms
**Tool: Web3Forms**
- Use Web3Forms (web3forms.com) for all customer website contact forms.
- Account: monty.mtuprojects@gmail.com
- Endpoint: `https://api.web3forms.com/submit`
- Each client site gets its own form created under the MTU Projects Web3Forms account.
- Hidden fields required on every form:
  ```html
  <input type="hidden" name="access_key" value="[CLIENT_ACCESS_KEY]">
  <input type="hidden" name="subject" value="New enquiry from [Client Site Name]">
  <input type="hidden" name="from_name" value="[Client Site Name] Website">
  ```
- Use AJAX fetch submission (no page redirect). Check `data.success` from response JSON.
- Free tier: 250 submissions/month per form. Sufficient for early-stage clients.

### Calendly Booking
- Use Calendly for "Book a free chat" / "Chat Now!" CTAs.
- MTU Projects Calendly: https://calendly.com/montyukpabio
- Client sites may use their own Calendly links — always confirm before building.

### Branding
- Colours: Forest Green `#556653`, Charcoal `#1E1E20`, White `#FFFFFF`, Light Grey `#E8E8E8`, Mid Grey `#7B7B7B`
- Font: Poppins (Bold for headings, Regular for body) via Google Fonts
- Primary button label: "Chat Now!" or "Book a free chat"
- Button style: rounded corners, forest green background, white text

### Tech Stack
- Plain HTML / CSS / JS — no page builders, no frameworks unless specifically needed
- Google Fonts for Poppins
- Web3Forms for contact forms
- Calendly for booking CTAs
- No unnecessary libraries

### Services Offered (as of 2025)
1. Website Build — homepage, about page, contact page
2. Simple Automations — enquiry auto-replies, reminders, lead routing
3. Ongoing Management — hosting, updates, automation adjustments (monthly fee)

---

## Contact Details (always use these)
- Phone: +44 7754 208536
- Email: info@mtuprojects.com
- Web: www.mtuprojects.com
- Location: Leeds, UK

---

*Last updated: August 2025*
