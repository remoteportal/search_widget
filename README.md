# Search Widget ![Cirrus CI - Base Branch Build Status](https://img.shields.io/cirrus/github/apgapg/search_widget) [![GitHub stars](https://img.shields.io/github/stars/apgapg/search_widget.svg?style=social)](https://github.com/apgapg/search_widget) [![Twitter Follow](https://img.shields.io/twitter/url/https/@ayushpgupta.svg?style=social)](https://twitter.com/ayushpgupta) ![GitHub last commit](https://img.shields.io/github/last-commit/apgapg/search_widget.svg) [![Website shields.io](https://img.shields.io/website-up-down-green-red/http/shields.io.svg)](https://play.google.com/store/apps/details?id=com.coddu.flutterprofile) [![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/apgapg/search_widget) [![style: effective dart](https://img.shields.io/badge/style-effective_dart-40c4ff.svg)](https://github.com/tenhobi/effective_dart)



This Flutter package provides a Search Widget for selecting an option from a data list. Provides filtering of items based on the search text.

<img src="https://raw.githubusercontent.com/apgapg/search_widget/master/src/s1.gif"  height = "400" alt="PieChart">

# 💻 Installation
In the `dependencies:` section of your `pubspec.yaml`, add the following line:

[![Version](https://img.shields.io/pub/v/search_widget.svg)](https://pub.dartlang.org/packages/search_widget)

```yaml
dependencies:
  search_widget: <latest version>
```

# ❔ Usage

### Import this class

```dart
import 'package:search_widget/search_widget.dart';
```

### Add Search Widget

- Accepts data list as input
- Option for getting selected item. Returns selected item or null if item is deleted
```dart
onItemSelected: (item) {
    //Do whatever you would like
    setState(() {
       _selectedItem = item;
    });
 },
```
- Option for pop list item builder. This basically returns a widget to show as list item in popup
```dart
popupListItemBuilder: (LeaderBoard item) {
   return PopupListItem(item);
 }
```
- Option for filtering data list based on search query
```dart
queryBuilder: (String query, List<LeaderBoard> list) {
   return list.where((LeaderBoard item) => item.username.toLowerCase().contains(query.toLowerCase())).toList();
 }
```
- Option provided for selected list item builder which enables when a user selects an item from pop up list
```dart
selectedItemBuilder: (LeaderBoard selectedItem, deleteSelectedItem) {
   return SelectedItem(selectedItem,deleteSelectedItem);
 }
```
- Option for providing custom TextField. Accepts TextEditingController and FocusNode as parameter
```dart
textFieldBuilder: (TextEditingController controller, FocusNode focusNode) {
    return TextField(
        controller: controller,
        focusNode: focusNode,
        //... Other customizations here
       );
  },
```
### Full Implementation

```dart
SearchWidget<LeaderBoard>(
   dataList: list,
   hideSearchBoxWhenItemSelected: false,
   listContainerHeight: MediaQuery.of(context).size.height / 4,
   queryBuilder: (String query, List<LeaderBoard> list) {
     return list.where((LeaderBoard item) => item.username.toLowerCase().contains(query.toLowerCase())).toList();
   },
   popupListItemBuilder: (LeaderBoard item) {
     return PopupListItemWidget(item);
   },
   selectedItemBuilder: (LeaderBoard selectedItem, VoidCallback deleteSelectedItem) {
     return SelectedItemWidget(selectedItem, deleteSelectedItem);
   },
   // widget customization
   noItemsFoundWidget: NoItemsFound(),
   textFieldBuilder: (TextEditingController controller, FocusNode focusNode) {
     return MyTextField(controller, focusNode);
   },
 )
```
### Key Highlights

- Adaptive Popup Position to prevent popup getting hidden behind keyboard   

<img src="https://raw.githubusercontent.com/apgapg/search_widget/master/src/s2.gif"  height = "400" alt="PieChart"> <img src="https://raw.githubusercontent.com/apgapg/search_widget/master/src/s1.gif" style="margin: 0px 4px"  height = "400" alt="PieChart">

  
- Popup to scroll with scroll gesture if this widget is used inside ScrollView  

<img src="https://raw.githubusercontent.com/apgapg/search_widget/master/src/s3.gif"  height = "400" alt="PieChart">

## TODO

- [X] Give support for onItemSelected method to return selected item(s) directly
- [ ] Add support for selecting multiple items
- [ ] Add visibility bool to show selected item widget

# ⭐ My Flutter Packages
- [pie_chart](https://pub.dartlang.org/packages/pie_chart)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/pie_chart.svg?style=social)](https://github.com/apgapg/pie_chart)  Flutter Pie Chart with cool animation.
- [avatar_glow](https://pub.dartlang.org/packages/avatar_glow)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/avatar_glow.svg?style=social)](https://github.com/apgapg/avatar_glow)  Flutter Avatar Glow Widget with glowing animation.
- [json_table](https://pub.dartlang.org/packages/json_table)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/json_table.svg?style=social)](https://github.com/apgapg/json_table)  Create Flutter Json Table from json map directly.
- [animating_location_pin](https://pub.dev/packages/animating_location_pin)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/animating_location_pin.svg?style=social)](https://github.com/apgapg/animating_location_pin)  Flutter Animating Location Pin Widget providing Animating Location Pin Widget which can be used while fetching device location.
          
# ⭐ My Flutter Apps
- [flutter_profile](https://github.com/apgapg/flutter_profile)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/flutter_profile.svg?style=social)](https://github.com/apgapg/flutter_profile)  Showcase My Portfolio: Ayush P Gupta on Playstore.
- [flutter_sankalan](https://github.com/apgapg/flutter_sankalan)  [![GitHub stars](https://img.shields.io/github/stars/apgapg/flutter_sankalan.svg?style=social)](https://github.com/apgapg/flutter_sankalan)  Flutter App which allows reading/uploading short stories.

# 👍 Contribution
1. Fork it
2. Create your feature branch (git checkout -b my-new-feature)
3. Commit your changes (git commit -m 'Add some feature')
4. Push to the branch (git push origin my-new-feature)
5. Create new Pull Request
