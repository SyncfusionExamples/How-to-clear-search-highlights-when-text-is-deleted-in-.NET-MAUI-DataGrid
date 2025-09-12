# How to clear search highlights when text is deleted in .NET MAUI DataGrid?

This article demonstrates how to clear search highlights when text is deleted in [.NET MAUI DataGrid](https://www.syncfusion.com/maui-controls/maui-datagrid).

In SfDataGrid with a search bar, the search text can be cleared either by clicking the clear (✕) icon or by manually deleting the text. To handle this, subscribe to the TextChanged event of the search bar. This event is triggered whenever the text changes, including when it is cleared. In the event handler, use the [SearchController](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.DataGrid.DataGridSearchController.html).[ClearSearch()](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.DataGrid.DataGridSearchController.html#Syncfusion_Maui_DataGrid_DataGridSearchController_ClearSearch) method to clear the search highlights.

## XAML

```xml
<Grid RowDefinitions="Auto,*">
    <HorizontalStackLayout Grid.Row="0" Spacing="10" Margin="10">
        <SearchBar x:Name="searchBar"
                   Placeholder="Search orders..."
                   SearchButtonPressed="searchBar_SearchButtonPressed"
                   TextChanged="searchBar_TextChanged"
                   WidthRequest="300"/>
    </HorizontalStackLayout>


    <syncfusion:SfDataGrid Grid.Row="1"
        x:Name="dataGrid"
        ItemsSource="{Binding OrderInfoCollection}">
        
        <syncfusion:SfDataGrid.Columns>
            <syncfusion:DataGridNumericColumn HeaderText="Order ID" Format="0"
            MappingName="OrderID" Width="150"/>
            <syncfusion:DataGridTextColumn HeaderText="Customer ID"
            MappingName="CustomerID"
            Width="150" />
            <syncfusion:DataGridTextColumn HeaderText="Ship Country"
            MappingName="ShipCountry"
            Width="150" />
        </syncfusion:SfDataGrid.Columns>
        
    </syncfusion:SfDataGrid>
</Grid>
```

## C#

```c#
private void searchBar_TextChanged(object sender, TextChangedEventArgs e)
{

    if (string.IsNullOrWhiteSpace(e.NewTextValue))
    {
        dataGrid.SearchController.ClearSearch();
    }

}
```

Download the complete sample from [GitHub](https://github.com/SyncfusionExamples/How-to-clear-search-highlights-when-text-is-deleted-in-.NET-MAUI-DataGrid)