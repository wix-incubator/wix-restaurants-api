Integrating any online ordering system with a POS (point-of-sale) system requires dealing with three issues:

* Menu management and synchronization
* Order submission and handling
* Payment processing

### Menu management and synchronization
Wix Restaurants supports three use cases for menu management.

1. **POS-based**: If the POS offers a web-based API for accessing menu data, Wix Restaurants can pull the data in real-time.
2. **Wix-based**: Menu data is managed in Wix Restaurants, and periodically exported to the POS using the Wix Restaurants API.
3. **Independent**: Menu data is managed in both systems independently, with Wix Restaurants items manually linked to the POS items by ID.

### Order submission and handling
Wix Restaurants supports two use cases for sending orders to the POS.

1. **Push**: [Wix Restaurants POS SPI](Wix-Restaurants-POS-(point-of-sale)-SPI) defines a simple webhook-based protocol that lets POS systems receive orders in real-time. This is our preferred integration method, as it offers the best customer experience.
2. **Pull**: The POS can periodically (e.g. every 1 minute) query the Wix Restaurants API for new orders, import them, and mark them as accepted or rejected.

### Payment processing
Wix Restaurants supports two use cases for processing customer payments.

1. **By the POS**: Payment information is securely transferred to the POS for clearing. The POS must be PCI level 1 compliant.
2. **By Wix Restaurants**: Wix Restaurants clears payments using a 3rd-party payment processor.
