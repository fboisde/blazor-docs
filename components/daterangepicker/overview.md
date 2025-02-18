---
title: Overview
page_title: DateRange Picker Overview
description: Overview of the Date Range Picker for Blazor.
slug: daterangepicker-overview
tags: telerik,blazor,date,range,picker,daterangepicker,overview
published: True
position: 0
---

# Blazor DateRange Picker Component Overview

The <a href="https://www.telerik.com/blazor-ui/daterange-picker" target="_blank">Blazor DateRange Picker component</a> allows the user to select a date range (start and end date) - both from a visual list ([calendar]({%slug components/calendar/overview%})) or to type it into a [date input]({%slug components/dateinput/overview%}) that can accept only dates. You can control the format shown in the input, and dates the user cannot select, as well as implement validation and respond to events.

## Creating Blazor Date Range Picker

1. Use the `TelerikDateRangePicker` tag to add the component to your razor page.
1. Bind its `StartValue` and `EndValue` parameters to `DateTime` objects
1. Optionally, provide custom `Format`, `Min` and `Max` values 


>caption Basic Date Range Picker with custom format, min and max

````CSHTML
@StartValue?.ToString("dd MMM yyyy")
<br />
@EndValue?.ToString("dd MMM yyyy")
<br />
<TelerikDateRangePicker @bind-StartValue="@StartValue"
                        @bind-EndValue="@EndValue"
                        Format="dd MMMM yyyy"
                        Min="@Min" Max="@Max">
</TelerikDateRangePicker>

@code {
    public DateTime? StartValue { get; set; } = DateTime.Now;
    public DateTime? EndValue { get; set; } = DateTime.Now.AddDays(10);
    public DateTime Min = new DateTime(1990, 1, 1, 8, 15, 0);
    public DateTime Max = new DateTime(2025, 1, 1, 19, 30, 45);
}
````

## Events

The Blazor Date Range Picker generates events that you can handle and further customize its behavior. [Read more about the Blazor Date Range Picker events...]({%slug daterangepicker-events %}).

## Validation

You can ensure that the component value is acceptable by using the built-in validation. [Read more about input validation...]({%slug common-features/input-validation%}).

To restrict the user from writing dates in the input so that the end is after the start, you must implement a custom data annotation attribute (you can find an example in the article linked above). The DateRangePicker component does not do this out-of-the-box in order to provide smooth user experience - the code cannot know what the user intent is and they might fix the range if they are given the chance, so correcting the input immediately may prevent them from using it comfortably. The component can fully control the user experience in the popup calendar and it ensures there that the range values are valid (start is before the end). If the user chooses an end date before the start, this date becomes the new start and they can choose the end again.

## Header Template

The DateRangePicker allows you to customize the rendering of the Calendar popup header. Learn more from the [Header Template article]({%slug daterangepicker-header-template%}).

## Adaptive Rendering

@[template](/_contentTemplates/dropdowns/adaptive-rendering.md#intro)

## DateRangePicker Parameters

The Blazor Date Range Picker provides various parameters that allow you to configure the component. Also check the [DateRangePicker's public API](/blazor-ui/api/Telerik.Blazor.Components.TelerikDateRangePicker-1).

@[template](/_contentTemplates/common/parameters-table-styles.md#table-layout)

| Attribute | Type and Default Value | Description |
|----------|----------|----------|
| `AdaptiveMode` | `AdaptiveMode` <br /> (`None`) | The [adaptive mode]({%slug adaptive-rendering%}) of the component. |
| `BottomView` | ` CalendarView` enum <br/> (`Month`) | Defines the bottommost view in the popup calendar to which the user can navigate to. |
| `DebounceDelay` | `int` <br/> (`150`) | Time in milliseconds between the last typed symbol and the value update. Use it to balance between client-side performance and number of database queries. |
| `DisabledDates` | `List<DateTime>` | A list of dates that can not be selected as the start or end of the range. See the <a href="https://demos.telerik.com/blazor-ui/daterangepicker/disabled-dates" target="_blank">Live Demo: Date Range Picker Disabled Dates</a>. |
| `Enabled` | `bool` | Whether typing in the inputs is allowed. |
| `Format` | `string` | The format of the DateInputs of the DateRangePicker. [Read more about supported data formats in Telerik DateInput for Blazor UI]({%slug components/dateinput/supported-formats%}) article. |
| `EndId` and `StartId` | `string` | The `id` attribute on the `<input />` element, so you can attach a `<label for="">` to the input. |
| `Min` | `DateTime` | The earliest date that the user can select. |
| `Max` | `DateTime` | The latest date that the user can select. |
| `Orientation` | `CalendarOrientation`enum <br /> (`Horizontal`) | The orientation of the calendar popup. The available options are `Horizontal` and `Vertical`. |
| `StartValue` and `EndValue` | `T` | The current values of the inputs for start and end of the range. Can be used for two-way binding. |
| `View` | ` CalendarView` enum <br/> (`Month`) | The current view that will be displayed in the popup calendar. |
| `TabIndex` | `int?` | The `tabindex` attribute of both `input` HTML elements in the component. They both will have the same `tabindex`. Use it to customize the tabbing (focus) order of the inputs on your page. |
| `Title` | `string` | The title text rendered in the header of the popup(action sheet). Applicable only when [`AdaptiveMode` is set to `Auto`]({%slug adaptive-rendering%}). |
| `Placeholder` |`string` | The `placeholder` attribute of the two `<input />` elements. The `Placeholder` will appear if the component is bound to **nullable** DateTime objects - `DateTime?`, but will not be rendered if the component is bound to the default value of a non-nullable DateTime objects. The Placeholder value will be displayed when the input is not focused. Once the user focuses it to start typing, the Format Placeholder (default or [customized one](#format-placeholder)) will override the Placeholder to indicate the format the date should be entered in. |

The date range picker is, essentially, a [date input]({%slug components/dateinput/overview%}) and a [calendar]({%slug components/calendar/overview%}) and the properties it exposes are mapped to the corresponding properties of these two components. You can read more about their behavior in the respective components' documentation.

### Styling and Appearance

The following parameters enable you to customize the appearance of the Blazor Date Range Picker:

| Attribute | Type and Default Value | Description |
|----------|----------|----------|
| `Class` | `string` | The CSS class that will be rendered on the main wrapping element of the Date Range Picker.
| `PopupClass` | `string` | additional CSS class to customize the appearance of the Date Range Picker's dropdown.

You can find more options for customizing the Date Range Picker styling in the [Appearance article]({%slug daterangepicker-appearance%}).

@[template](/_contentTemplates/date-inputs/format-placeholders.md#format-placeholder)

## DateRangePicker Reference and Methods

Add a reference to the component instance to use the [Date Range Picker's methods](/blazor-ui/api/Telerik.Blazor.Components.TelerikDateRangePicker-1).

| Method | Description |
| --- | --- |
| `Close` | Closes the Calendar popup. |
| `FocusStartAsync` | Focuses the Date Range Picker start value textbox. Always `await` this call, as it relies on `JSInterop`. |
| `FocusEndAsync` | Focuses the Date Range Picker end value textbox. Always `await` this call, as it relies on `JSInterop`.|
| `NavigateTo` | Navigates to a specified date and view. The method expects a `DateTime` and `CalendarView` arguments. |
| `Open` | Opens the Calendar popup. |
| `Refresh` | Re-renders the Calendar popup. |


````CSHTML
<TelerikButton OnClick="@FocusStart">Focus Start TextBox</TelerikButton>
<TelerikButton OnClick="@FocusEnd">Focus End TextBox</TelerikButton>
<TelerikButton OnClick="@OpenPicker">Open DateRangePicker</TelerikButton>

<TelerikDateRangePicker @ref="@DateRangePickerRef"
                        @bind-StartValue="@DateRangePickerStartValue"
                        @bind-EndValue="@DateRangePickerEndValue" />

@code {
    // the component type depends on the value type, could be also DateTime?
    private TelerikDateRangePicker<DateTime> DateRangePickerRef { get; set; }

    private DateTime DateRangePickerStartValue { get; set; } = DateTime.Now;

    private DateTime DateRangePickerEndValue { get; set; } = DateTime.Now.AddDays(10);

    private async Task FocusStart()
    {
        await DateRangePickerRef.FocusStartAsync();
    }

    async Task FocusEnd()
    {
        await DateRangePickerRef.FocusEndAsync();
    }

    void OpenPicker()
    {
        DateRangePickerRef.Open();
    }
}
````

## Next Steps

* [Using the Date Range Picker Events]({%slug daterangepicker-events%})

## See Also

  * [Live Demo: Date Range Picker](https://demos.telerik.com/blazor-ui/daterangepicker/overview)
  * [Input Validation]({%slug common-features/input-validation%})
  * [Supported Input Date Formats]({%slug components/dateinput/supported-formats%})
  * [API Reference](https://docs.telerik.com/blazor-ui/api/Telerik.Blazor.Components.TelerikDateRangePicker-1)
