# Order status workflow

Selected excerpt from the private implementation showing the canonical status vocabulary and the forward-only Seller transitions.

```csharp
private static readonly string[] CanonicalOrderStatuses =
{
    "Ne Procesim",
    "E Verifikuar",
    "E Pergaditur",
    "E Dorezuar Tek Postieri",
    "E Pranuar nga Klienti"
};

private static readonly IReadOnlyDictionary<string, string> SalesNextStatuses =
    new Dictionary<string, string>(StringComparer.OrdinalIgnoreCase)
    {
        ["Ne Procesim"] = "E Verifikuar",
        ["E Verifikuar"] = "E Pergaditur"
    };
```

Administrator corrections and the remaining transition rule are enforced in the backend; this excerpt is deliberately partial.
