# AGUDATECH IT Solutions — eSIM Web Design Sample

A responsive eSIM storefront experience designed and produced under **AGUDATECH IT Solutions**. The initial concept is preserved in [`prototype.html`](./prototype.html), a standalone interactive demo that presents the complete purchase journey in one file.

## Design Highlights

- Seven connected screens: home, plan browsing, plan details, cart, checkout, payment processing, and eSIM delivery
- Responsive layouts for desktop and mobile viewports
- Clear pricing, coverage, and carrier comparisons
- Local payment options represented through GCash, Maya, and card flows
- Bilingual English and Filipino microcopy
- Delivery and activation guidance presented as part of the post-purchase experience
- Consistent sky-blue visual system, rounded cards, status badges, and focused calls to action

## Sample Screenshots

| Home | Plan browsing | Successful delivery |
| --- | --- | --- |
| <img src="./docs/screenshots/esim-home.png" alt="Responsive eSIM storefront home screen" width="100%"> | <img src="./docs/screenshots/esim-plans.png" alt="eSIM plan browsing screen with carrier and coverage cards" width="100%"> | <img src="./docs/screenshots/esim-success.png" alt="Successful eSIM delivery screen with activation details" width="100%"> |

## Architecture and Technology Stack

```mermaid
flowchart LR
    Visitor([Visitor])

    subgraph Browser["Browser experience"]
        Prototype["prototype.html<br/>HTML + Tailwind CDN + Vanilla JavaScript"]
        NextApp["Next.js 14 App Router<br/>React + TypeScript"]
    end

    Assets["External assets<br/>Tailwind CDN + Google Fonts"]
    UI["Shared UI components<br/>Tailwind CSS"]
    Catalog[("lib/plans.ts<br/>Static plan catalog")]
    Mocked["Mocked cart, checkout,<br/>payment, and delivery states"]

    Visitor -->|Opens standalone demo| Prototype
    Visitor -->|Runs current application| NextApp
    Assets --> Prototype
    Prototype -->|show changes active screen| Mocked
    NextApp --> UI
    UI --> Catalog
    UI --> Mocked
```

## Happy Flow

```mermaid
sequenceDiagram
    autonumber
    actor Visitor
    participant UI as Storefront UI
    participant Catalog as Static plan catalog
    participant Checkout as Cart and checkout
    participant Payment as Simulated payment
    participant Delivery as Delivery screen

    Visitor->>UI: Browse available plans
    UI->>Catalog: Read plan data
    Catalog-->>UI: Return pricing, coverage, and features
    Visitor->>UI: Select a plan
    UI->>Checkout: Add plan and continue
    Visitor->>Checkout: Enter details and choose payment method
    Checkout->>Payment: Submit demonstration payment
    Payment-->>Checkout: Show processing state
    Payment->>Delivery: Complete simulated purchase
    Delivery-->>Visitor: Show QR and activation guidance

    Note over Checkout,Delivery: Demonstration only, with no live service calls or persistence
```

## View the Original Prototype

The prototype is plain HTML with lightweight JavaScript navigation. It loads Tailwind CSS and Inter from external CDNs, so an internet connection is required for the intended styling.

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000/prototype.html](http://localhost:8000/prototype.html). Use the flow controls at the top or the in-page actions to move through the experience.

## Technology

- HTML5
- Tailwind CSS via CDN
- Vanilla JavaScript
- Google Fonts — Inter

## Current Implementation

The repository also contains a Next.js 14 and TypeScript implementation of the same core design direction. Run it with:

```bash
npm ci
npm run dev
```

The purchase experience is a design demonstration: product data, payment states, order details, and QR information are illustrative rather than connected to live services.

---

**Designed and produced by AGUDATECH IT Solutions.**


## Contribution

This project is open for collaboration. If you wish to contribute:

    Fork the repository.
    Create a feature branch (git checkout -b feature/your-feature-name).
    Commit your changes (git commit -m 'Add your feature').
    Push to the branch (git push origin feature/your-feature-name).
    Open a pull request.

## Contact

For any questions or inquiries, please reach out to www.linkedin.com/in/agudatech/.

## Support

If you find this project helpful and would like to support its ongoing development, consider buying me a coffee! Your support helps me keep working on this project and developing more features.

[![Buy Me a Coffee](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://www.buymeacoffee.com/mauriceague)
