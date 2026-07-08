# ViewModelBase

`ViewModelBase` is a reusable base class for WPF MVVM applications.

It implements `INotifyPropertyChanged` and provides the `OnPropertyChanged()` method, which allows bound UI elements to update automatically when a property value changes.

## Example

```csharp
public class PersonViewModel : ViewModelBase
{
    private string name;

    public string Name
    {
        get => name;
        set
        {
            name = value;
            OnPropertyChanged();
        }
    }
}
```