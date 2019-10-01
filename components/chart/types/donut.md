---
title: Donut
page_title: Chart for Blazor | Donut
description: Overview of the Donut Chart for Blazor
slug: components/chart/types/donut
tags: telerik,blazor,chart,donut
published: True
position: 0
---

# Donut Chart

The **Donut** chart displays the data as sectors from a two-dimensional circle and is therefore useful for displaying data as parts of a whole. Unlike a pie chart, it can have multiple series in the same chart. There is a hole in the middle of the circle, hence the name of the chart.

>caption Donut chart. Results from the first code snippet below

![](images/basic-donut-chart.png)

@[template](/_contentTemplates/chart/link-to-basics.md#understand-basics-and-databinding-first)

To create a donut chart:

1. add a `ChartSeries` to the `ChartSeriesItems` collection
2. set its `Type` property to `ChartSeriesType.Donut`
3. provide a data model collection to its `Data` property
4. set the `Field` and `CategoryField` properties to the corresponding fields in the model that carry the values and names that will be shown in the legend

If you use [simple data binding]({%slug components/chart/databind%}#independent-series-binding) and only provide values, the chart will not render a legend.

>caption A donut chart that shows product revenues

````CSHTML
Donut series

<TelerikChart>
	<ChartSeriesItems>
		<ChartSeries Type="ChartSeriesType.Donut" Data="@donutData" 
							Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
		</ChartSeries>
	</ChartSeriesItems>

	<ChartTitle Text="Revenue per product"></ChartTitle>

	<ChartLegend Position="ChartLegendPosition.Right">
	</ChartLegend>
</TelerikChart>

@code {
	public class MyDonutChartModel
	{
		public string SegmentName { get; set; }
		public double SegmentValue { get; set; }
		public bool ShouldShowInLegend { get; set; } = true;
	}
	
	public List<MyDonutChartModel> donutData = new List<MyDonutChartModel>
	{
		new MyDonutChartModel
		{
			SegmentName = "Product 1",
			SegmentValue = 2
		},
		new MyDonutChartModel
		{
			SegmentName = "Product 2",
			SegmentValue = 3
		},
		new MyDonutChartModel
		{
			SegmentName = "Product 3",
			SegmentValue = 4
		}
	};
}
````



## Donut Chart Specific Appearance Settings

The donut chart is a variation of the Pie Chart graph type, and has the same features and behavior. You can read more about them in the [Pie Chart]({%slug components/chart/types/pie%}#pie-chart-specific-appearance-settings) article.

### Hole Size

You can change the percentage that the hole in the middle takes from the entire diameter of the circle by setting the `HoleSize` property of the series. Setting `0` removes the hole, and `100` means the entire chart is the hole.

````CSHTML
Control the hole size of the donut chart

<TelerikChart>
	<ChartSeriesItems>
		<ChartSeries Type="ChartSeriesType.Donut" Data="@donutData" HoleSize="90"
							Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
		</ChartSeries>
	</ChartSeriesItems>

	<ChartTitle Text="Revenue per product"></ChartTitle>

	<ChartLegend Position="ChartLegendPosition.Right">
	</ChartLegend>
</TelerikChart>

@code {
	public class MyDonutChartModel
	{
		public string SegmentName { get; set; }
		public double SegmentValue { get; set; }
		public bool ShouldShowInLegend { get; set; } = true;
	}
	
	public List<MyDonutChartModel> donutData = new List<MyDonutChartModel>
	{
		new MyDonutChartModel
		{
			SegmentName = "Product 1",
			SegmentValue = 2
		},
		new MyDonutChartModel
		{
			SegmentName = "Product 2",
			SegmentValue = 3
		},
		new MyDonutChartModel
		{
			SegmentName = "Product 3",
			SegmentValue = 4
		}
	};
}
````

>caption Comparison between the result of the code snippet above and the default behavior

![](images/donut-hole-size.png)

## Multiple Series

Unlike a pie chart, a donut chart can have multiple series in a single chart. Each series is nested in the next - the first declared series is in the center, and the last series is at the outer edge.

You can use multiple series to showcase relationships within a data set, or several similar sets of data.

You can also use the `ColorField` property to define a field with the segments' colors. With this, you can color-code different series and their relationships to one another.

>caption Multiple donut series in a single chart (code sample after the figure)

![](images/multiple-donut-series.png)

````CSHTML
@* You can bind the entire chart to one collection of data, even though this example shows separate collections for each series *@

<TelerikChart>
    <ChartSeriesItems>
        <ChartSeries Type="ChartSeriesType.Donut" Data="@firstSeriesData"
                     Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
        </ChartSeries>
        <ChartSeries Type="ChartSeriesType.Donut" Data="@secondSeriesData"
                     Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
        </ChartSeries>
        <ChartSeries Type="ChartSeriesType.Donut" Data="@thirdSeriesData"
                     Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
        </ChartSeries>
        <ChartSeries Type="ChartSeriesType.Donut" Data="@fourthSeriesData"
                     Field="@nameof(MyDonutChartModel.SegmentValue)" CategoryField="@nameof(MyDonutChartModel.SegmentName)">
        </ChartSeries>
    </ChartSeriesItems>

    <ChartTitle Text="Revenue per product"></ChartTitle>

    <ChartLegend Position="ChartLegendPosition.Right">
    </ChartLegend>
</TelerikChart>

@code {
    public class MyDonutChartModel
    {
        public string SegmentName { get; set; }
        public double SegmentValue { get; set; }
        public bool ShouldShowInLegend { get; set; } = true;
    }

    public List<MyDonutChartModel> firstSeriesData = new List<MyDonutChartModel>
    {
        new MyDonutChartModel
        {
            SegmentName = "Product Line 1",
            SegmentValue = 2
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 2",
            SegmentValue = 3
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 3",
            SegmentValue = 4
        }
    };

    public List<MyDonutChartModel> secondSeriesData = new List<MyDonutChartModel>
    {
        new MyDonutChartModel
        {
            SegmentName = "Product Line 1 - Product 1",
            SegmentValue = 4
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 1 - Product 2",
            SegmentValue = 7
        }
    };

    public List<MyDonutChartModel> thirdSeriesData = new List<MyDonutChartModel>
    {
        new MyDonutChartModel
        {
            SegmentName = "Product Line 2 - Product 1",
            SegmentValue = 1
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 2 - Product 2",
            SegmentValue = 5
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 2 - Product 3",
            SegmentValue = 2
        }
    };

    public List<MyDonutChartModel> fourthSeriesData = new List<MyDonutChartModel>
    {
        new MyDonutChartModel
        {
            SegmentName = "Product Line 3 - Product 1",
            SegmentValue = 6
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 3 - Product 2",
            SegmentValue = 11
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 3 - Product 3",
            SegmentValue = 2
        },
        new MyDonutChartModel
        {
            SegmentName = "Product Line 3 - Product 4",
            SegmentValue = 20
        }
    };
}
````

## See Also

  * [Live Demo: Donut Chart](https://demos.telerik.com/blazor-ui/chart/donut-chart)
