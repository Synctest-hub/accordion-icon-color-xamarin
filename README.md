# How to customize the Accordion icon color in Xamarin.Forms (SfAccordion)

You can customize the expander icon using [IconColor](https://help.syncfusion.com/cr/cref_files/xamarin/Syncfusion.Expander.XForms~Syncfusion.XForms.Accordion.AccordionItem~IconColor.html?) property of [SfAccordion](https://help.syncfusion.com/xamarin/accordion/getting-started?) in Xamarin.Forms.

You can also refer the following article.

https://www.syncfusion.com/kb/11443/how-to-customize-the-accordion-icon-color-in-xamarin-forms-sfaccordion

**C#**

Defining **IconColor** property in **Model**.
``` c#
namespace AccordionXamarin
{
    public class ItemInfo : INotifyPropertyChanged
    {
        private Color _iconColor;
 
        public Color IconColor
        {
            get => _iconColor;
            set
            {
                _iconColor = value;
                OnPropertyChanged("IconColor");
            }
        }
 
        public event PropertyChangedEventHandler PropertyChanged;
 
        private void OnPropertyChanged(string Property)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(Property));
        }
    }
}
```
**C#**

Populating **IconColor** in **ViewModel**.
``` c#
namespace AccordionXamarin
{
    public class ItemInfoRepository
    {
        public ObservableCollection<ItemInfo> Info { get; set; }
 
        public ItemInfoRepository()
        {
            Info = new ObservableCollection<ItemInfo>();
            Info.Add(new ItemInfo() { IconColor = Color.DarkOrange });
            Info.Add(new ItemInfo() { IconColor = Color.DarkBlue });
            Info.Add(new ItemInfo() { IconColor = Color.DarkRed });
            Info.Add(new ItemInfo() { IconColor = Color.DarkViolet });
        }
 
    }
}
```
**XAML**

Binding Accordion **IconColor** property with **Model** Property.
``` xml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:syncfusion="clr-namespace:Syncfusion.XForms.Accordion;assembly=Syncfusion.Expander.XForms"
             x:Class="AccordionXamarin.MainPage" Padding="{OnPlatform iOS='0,40,0,0'}">
 
    <ContentPage.Content>
        <syncfusion:SfAccordion x:Name="Accordion" ExpandMode="SingleOrNone" Margin="5" BindableLayout.ItemsSource="{Binding Info}">
            <BindableLayout.ItemTemplate>
                <DataTemplate>
                    <syncfusion:AccordionItem IconColor="{Binding IconColor}" x:Name="AccordionItem">
                        <syncfusion:AccordionItem.Header>
                            <Grid HeightRequest="50">
                                <Label Text="{Binding Name}" VerticalOptions="Center" HorizontalOptions="StartAndExpand"/>
                            </Grid>
                        </syncfusion:AccordionItem.Header>
                        <syncfusion:AccordionItem.Content>
                            <Grid Padding="5" BackgroundColor="NavajoWhite">
                                <Label Text="{Binding Description}"/>
                            </Grid>
                        </syncfusion:AccordionItem.Content>
                    </syncfusion:AccordionItem>
                </DataTemplate>
            </BindableLayout.ItemTemplate>
        </syncfusion:SfAccordion>
    </ContentPage.Content>
</ContentPage>
```
**Output**

![AccordionIconColor](https://github.com/SyncfusionExamples/accordion-icon-color-xamarin/blob/master/ScreenShots/AccordionIconColor.png)
