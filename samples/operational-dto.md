# Operational response DTO

Selected excerpt from the private implementation. The operational list returns a deliberately narrow shape instead of exposing an entity graph.

```csharp
public sealed class OperationalOrderStatusDto
{
    public int IdPorosia { get; init; }
    public string? StatusiPorosis { get; init; }
}
```

The complete application uses related DTOs for the table view; this small response illustrates the principle of returning only fields needed by the operation.
