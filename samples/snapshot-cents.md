# Payment snapshot calculation

Selected excerpt from the private implementation: converting decimal amounts to minor units and deriving the payment snapshot total from immutable line values.

```csharp
public static long ToMinor(decimal amount) =>
    checked(decimal.ToInt64(
        decimal.Round(amount * 100m, 0, MidpointRounding.AwayFromZero)));

var subtotal = lines.Sum(x => x.LineTotalMinor);
var discountMinor = cartDiscountIsActive
    ? ToMinor(cartDiscount)
    : 0L;
var transportMinor = ToMinor(transportAmount);
var amount = subtotal - discountMinor + transportMinor;

if (amount <= 0 || discountMinor > subtotal)
    throw new InvalidOperationException("Invalid payment total.");
```

The excerpt demonstrates the cents/minor-unit boundary without exposing cart identifiers, customer data, or payment credentials.
