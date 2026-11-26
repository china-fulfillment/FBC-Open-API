# FBC China Fulfillment Service Integration
FBC (FulfillmentByChina) OpenAPI for China fulfillment and dropshipping. Automate inbound, inventory sync, order creation, label generation, tracking and logistics quotes. Integrate with Shopify, WooCommerce, Amazon and ERPs. Supports private packing, QC, DDP/DDU shipping, SN management, webhooks and sandbox for secure cross-border order automation
# FBC OpenAPI
> OpenAPI for China‑based fulfillment & China dropshipping WMS integration

FBC (FulfillmentByChina) delivers warehouse fulfillment and dropshipping OpenAPI for cross‑border e‑commerce merchants, ERPs and SaaS platforms. Automate the full operational workflow including product setup, inbound receiving, real‑time inventory lookup, outbound order submission, logistics rate quotation, shipping label upload and shipment tracking. Integrate seamlessly with Shopify, WooCommerce, Amazon and custom in‑house systems. Supports general goods, bulk cargo, customer returns, customs declaration fields, IOSS, VAT and COD cross‑border scenarios.

## ✨ Supported Services
- **Product Management**: Create, query and list product records. Maintain SKU data, customs attributes, dimension‑weight info and battery/dangerous‑goods metadata.
- **Inbound Warehouse Operations**: Create/cancel inbound orders, fetch inbound status, download carton labels. Supports standard inbound, customer return receiving and bulk‑goods inbound.
- **Inventory Management**: Single‑SKU inventory query, paginated inventory listing and stock lot traceability for real‑time available stock visibility.
- **Outbound Fulfillment & Dropshipping**: Create small‑parcel and bulk outbound orders, cancel outbound jobs, upload external PDF shipping labels.
- **Logistics & Shipping**: Retrieve warehouse list, fetch available shipping services, calculate shipping rates and pull shipment tracking events.
- **Cross‑border Compliance**: IOSS, VAT ID, COD cash‑on‑delivery, battery UN number, HS‑code and country‑of‑origin declaration.

## 📂 Repository Assets
- `FBC‑ChinaFulFillment.json`: Swagger 2.0 OpenAPI specification for WMS warehouse business endpoints
- Code Samples: Coming soon
- Postman Collection: Coming soon

## 🔐 Authentication
This API uses custom header‑based signature authentication. Every HTTP request must include three headers:

| Header | Description |
|---|---|
| `client_id` | Customer ID, obtained from backend `My Account > API Interface` |
| `timestamp` | Unix millisecond timestamp, **valid within 5 minutes** |
| `client_secret` | 32‑bit uppercase MD5 hash of `customerId + apiKey + timestamp` |

> ⚠️ Compute signature on your backend server. Never expose your apiKey in frontend client‑side code.

## 📋 API Module Overview
1. **Basis**: Fetch warehouse catalog and available shipping services
2. **Product**: Create, retrieve and paginate product records
3. **Inbound**: Inbound order creation, query, cancellation and carton label retrieval
4. **Inventory**: Stock query, inventory list and stock detail trace
5. **Outbound**: Small / bulk outbound creation, order cancellation, label upload, tracking inquiry and shipping rate calculation

**Base Host**: `https://app.fulfillmentbychina.com`

## 🚀 Quick Start
1. Login to FBC admin portal, navigate to `My Account > API Interface` to get your `customerId` and `apiKey`.
2. Import `FBC‑ChinaFulFillment.json` into a Swagger editor to inspect all endpoints and schemas.
3. Implement MD5 signature logic on your backend and assemble required request headers.
4. Call basic endpoints to obtain warehouse codes and shipping service codes before running inbound or outbound operations.

### Minimal HTTP Request Example
```http
GET /api/wms/Basis/Warehouse HTTP/1.1
Host: app.fulfillmentbychina.com
client_id: "10001"
timestamp: "1702172766695"
client_secret: "B73DD1CA8BE1688CEF24F425E3ECD1A3"
Accept: application/json
```

## 📝 Unified Response Schema
All API responses follow the `ApiResultModel` structure:
```json
{
  "code": 200,
  "data": {},
  "message": "success",
  "taskid": "uuid‑trace‑id"
}
```
- `code=200`: Business success; non‑200 values indicate errors. Read `message` for troubleshooting details.
- `taskid`: Unique trace identifier. Include this value when submitting support tickets.

##  Sandbox & Rate Limits
> Sandbox access: Contact FBC support to request sandbox developer credentials.
> Rate‑limit quota: Reach out to FBC support for your assigned QPS limits.

## Common Integration Use‑Cases
- Shopify / WooCommerce storefront dropshipping workflows
- Cross‑border ERP integration with China warehouse fulfillment
- B2B bulk‑goods outbound automation and return‑receiving pipelines
- Multi‑store unified inventory & order fulfillment orchestration

## License
This OpenAPI specification is available under the **MIT License**.

## Developer Support
- Developer Portal: Official FBC(FulfillmentByChina) developer documentation
- Technical Contact: support@fulfillmentbychina.com

---

If you need further artifacts such as signature code snippets (Python / C#), or a condensed one‑page README variant, just let me know.
