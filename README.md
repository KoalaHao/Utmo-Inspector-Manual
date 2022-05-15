# Utmo Inspector Manual

## What is Utmo Inspector

Utmo Inspector replaces the default unity inspector for `MonoBehaviour` and `Scriptable Object`

Utmo Inspector looks and feels like the default inspector, but offers high customization powered by the new UI Toolkit (AKA UI Elements). Utmo Inspector fully exploits the potential and advantages of UI Toolkit, providing better performance when compared to IMGUI inspectors. In addition, it can be changed on the fly without the tedious script compilation and domain reload.

Creating custom editors for your scripts is now a piece of cake; no programming is needed, no attributes need to be remembered, and no script recompilation or domain reloading is required.

## Customize a Script or Scriptable Object

Click on the edit button next to the script field to open the config editor for that script
![image](https://user-images.githubusercontent.com/19798828/168411471-f054ec6c-136b-4f4a-91b2-6441dacafb52.png)

Any changes you make will reflect immediately on the inspector, feel free to play around

`Reset to default` will revert all of the customization made to this script

Add items such as groups, buttons, properties and functions with the `Add Entry` button

In order to delete an item, select the item and click `Delete Entry`. You cannot delete Serialized fields, but you can set its visibility to never if you don't want to see them.

![image](https://user-images.githubusercontent.com/19798828/168411490-e90f7ba3-f464-457a-9905-70ff0f4afede.png)

Select an item to show and edit its properties

## Customize an entry

![image](https://user-images.githubusercontent.com/19798828/168411518-6e4f0e7c-a2b4-496b-9b3f-a283efb634b9.png)

`Alias` or `Name` (depending on what you selected) changes the label of the field

Adding a 'tooltip' to any field will display a text when the mouse is over it. It will also add a little circle to the field's label as an indication that someone has provided a tooltip to this field

`Visibility` controls if the entry can be seen, `Editable` controls if the entry is useable or otherwise disabled

`Custom Drawers` are optional drawers for displaying a value

### Visibility and Editable Options

|  | Visibility | Editable |
| --- | --- | --- |
| Always | default, always visible | always enabled and useable |
| Never | Hidden | disabled, greyed out |
| EditMode | visible in Edit Mode, hidden in Play Mode  | editable in Edit Mode, disabled in Play Mode |
| PlayMode | visible in Play Mode, hidden in Edit Mode | editable in play Mode, disabled in Edit Mode |
| When true | visible when a condition is met, otherwise hidden | editable when a condition is met, otherwise disabled |
| When false | visible when a condition is not met, otherwise hidden | editable when a condition is not met, otherwise disabled |

When `When true` or `When false` is selected, another dropdown field will be available which lists all possible values available to this script

The value of any type can be regarded as `true` if it is not the type's `default` value. For example, `float`s will have a default value of `0`, any value other than `0` will be considered `true`. Similarly, `GameObject`s will have a default value of `null`, if they are set and not `null`, they will be considered `true`.

For example, consider the following code

```csharp
public GameObject Gun;
public void Shoot(){...}
```

you want to display a `Shoot` button only if `Gun` gameObject is set. 

![visible](https://user-images.githubusercontent.com/19798828/168411532-26329672-8206-4c91-91e9-8b450fee1216.gif)


### Custom Drawer

Custom Drawers are useful to change the way your values are displayed and manipulated

Supported custom drawers for Utmo Inspector V 1.0 are:

| Type | Custom Drawer |
| --- | --- |
| string | TextArea |
| Color | HDR Color |
| Float | Slider |
|  | Progress Bar |
| bool | Toggle Left |

The list will continue to grow as Utmo Inspector updates. Feel free to make a suggestion by [raising an issue](https://github.com/KoalaHao/Utmo-Inspector-Manual/issues)

## Writing Custom Editor

Despite its powerful capabilities, Utmo Inspector focuses solely on the inspector part of the editor. Whenever you need to write an editor that interacts with the scene view, displays handles, etc, while still utilizing Utmo's inspector functionalities, just inherit your class from UtmoEditor instead of Editor.

From:

```csharp
[CustomEditor(typeof(MyScript))]
public classMyEditor: Editor
```

To:

```csharp
[CustomEditor(typeof(MyScript))]
public classMyEditor: UtmoEditor
```

## Version Control

Editor configurations are saved in the meta file, so "MyScript.cs" has its editor configuration stored in the "MyScript.cs.meta" file in the userdata section. Version control is supported, just commit and push the meta file, and the customized editor will be synchronized across the team.

## Support

Issues : [https://github.com/KoalaHao/Utmo-Inspector-Manual/issues](https://github.com/KoalaHao/Utmo-Inspector-Manual/issues)

RoadMap : [https://github.com/users/KoalaHao/projects/1](https://github.com/users/KoalaHao/projects/1/views/1)
