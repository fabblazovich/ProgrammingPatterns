# WPF MVVM Essentials

## ObservableObject

`ObservableObject` is provided by CommunityToolkit.Mvvm and automatically implements `INotifyPropertyChanged`.

Benefits:

- Less boilerplate code
- Automatic UI updates
- Modern MVVM approach

Example:

```csharp
public partial class MainWindowViewModel : ObservableObject
{
}
```

---
---

## ObservableProperty

`[ObservableProperty]` automatically generates a public property and notifies the UI when the value changes.

Example:

```csharp
[ObservableProperty]
private string name = string.Empty;
```

Generated property:

```csharp
public string Name { get; set; }
```

Usage:

```xml
<TextBox Text="{Binding Name}" />
```

---
---

## RelayCommand

`[RelayCommand]` automatically generates an `ICommand`.

Example:

```csharp
[RelayCommand]
private void Save()
{
}
```

Generated command:

```csharp
SaveCommand
```

Usage:

```xml
<Button Command="{Binding SaveCommand}" />
```

---
---

# Data Binding

Connects UI elements to ViewModel properties.

Example:

```xml
<TextBox Text="{Binding Name}" />
```

```csharp
[ObservableProperty]
private string name = string.Empty;
```

Whenever `Name` changes, the UI updates automatically.

---
---

# ObservableCollection

Used for collections displayed in the UI.

Example:

```csharp
public ObservableCollection<string> Names { get; }
    = new();
```

Binding:

```xml
<ListBox ItemsSource="{Binding Names}" />
```

Adding an item:

```csharp
Names.Add("Fabian");
```

The ListBox updates automatically.

---
---

# SelectedItem

Stores the currently selected item from a list.

ViewModel:

```csharp
[ObservableProperty]
private string selectedName = string.Empty;
```

View:

```xml
<ListBox ItemsSource="{Binding Names}"
         SelectedItem="{Binding SelectedName}" />
```

Display selected item:

```xml
<Label Content="{Binding SelectedName}" />
```

---
---

# Commands

Commands replace Click events in MVVM.

Without MVVM:

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
}
```

With MVVM:

```csharp
[RelayCommand]
private void Save()
{
}
```

```xml
<Button Command="{Binding SaveCommand}" />
```

---
---

# CurrentView Navigation

Simple MVVM navigation between UserControls.

ViewModel:

```csharp
[ObservableProperty]
private object currentView;
```

```csharp
CurrentView = new MaterialView();
```

View:

```xml
<ContentControl Content="{Binding CurrentView}" />
```

---
---

# MVVM Workflow

```text
View
  ↓
Binding
  ↓
ViewModel
  ↓
Property / Command
  ↓
UI updates automatically
```

---
---

# Typical MVVM Structure

```text
Project
│
├── Views
│   ├── MainWindow.xaml
│   └── MaterialView.xaml
│
├── ViewModels
│   ├── MainWindowViewModel.cs
│   └── MaterialViewModel.cs
│
├── Models
│   └── Material.cs
│
└── Services
```

---
---


# Application Resources

Application Resources provide a central location for managing colors, brushes, styles and templates across the entire WPF application.

## Benefits

- Consistent UI design
- Easier maintenance
- Reduced duplicate XAML code
- Centralized color management
- Easy theme changes

---

## App.xaml

```xml
<Application.Resources>

    <SolidColorBrush x:Key="HeaderBackgroundColor" Color="Green"/>

</Application.Resources>
```

---

## Usage

Use the resource anywhere in the application.

```xml
<Border Background="{StaticResource HeaderBackgroundColor}">
    <TextBlock Text="Header"/>
</Border>
```

---

## Define Multiple Colors

```xml
<Application.Resources>

    <SolidColorBrush x:Key="PrimaryBrush" Color="#4CAF50"/>

    <SolidColorBrush x:Key="SecondaryBrush" Color="#2196F3"/>

    <SolidColorBrush x:Key="WarningBrush" Color="#FF9800"/>

</Application.Resources>
```

Usage:

```xml
<Button Background="{StaticResource PrimaryBrush}" Content="Save"/>
```
