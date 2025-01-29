Custom Qt Quick Chart
Custom Qt Quick Chart is a QML component for adding custom charts/graphs to your Qt applications. This component provides a simple and flexible way to visualize data in real-time.

Features
Customizable line color
Adjustable maximum number of points
Transparent background
Circular buffer for efficient data management
Getting Started
To start using the Custom Qt Quick Chart component, follow these steps:

Add the Component to Your Project
Include the QML file in your Qt project.

Import the Required Modules
Ensure that you have the necessary Qt modules imported in your QML file:

QML
import QtQuick 2.15
import QtCharts 2.15
Usage
Here's an example of how to use the Custom Qt Quick Chart component in your QML file:

QML
Rectangle {
    id: graphComponent
    width: 800
    height: 300
    color: "transparent" // Transparent background
    border.width: 0

    property color graphColor: "#00ff00"
    property int maxPoints: 500        // Maximum number of points to show on the graph
    property real currentIndex: 0      // Current index for wrapping
    property real minValue: 0          // Minimum value for scaling
    property real maxValue: 200        // Maximum value for scaling
    property int blankSpace: 4         // Number of blank points to add at the front

    ChartView {
        id: chartView
        anchors.fill: parent
        antialiasing: true
        backgroundColor: "transparent" // Transparent background for the chart
        margins.left: 10
        margins.right: 0
        margins.top: 0
        margins.bottom: 0

        legend.visible: false // Remove the legend (small square on top)

        LineSeries {
            id: lineSeries
            color: graphComponent.graphColor
            axisX: xAxis
            axisY: yAxis
        }

        ValueAxis {
            id: xAxis
            min: 0
            max: graphComponent.maxPoints - 1 + graphComponent.blankSpace
            labelsVisible: false // Hide x-axis labels
            visible: false // Hide the axis line
        }

        ValueAxis {
            id: yAxis
            min: graphComponent.minValue
            max: graphComponent.maxValue
            labelsVisible: false // Hide y-axis labels
            visible: false // Hide the axis line
        }
    }

    Text {
        id: maxTxt
        anchors.top: parent.top
        anchors.leftMargin: 0
        anchors.topMargin: 2
        font.pixelSize: 14
        font.family: "Arial"
        color: graphComponent.graphColor
        text: Number(graphComponent.maxValue).toFixed(0)
        anchors.left: parent.left
    }

    Text {
        id: minTxt
        anchors.bottom: parent.bottom
        anchors.leftMargin: 0
        anchors.bottomMargin: 2
        font.pixelSize: 14
        font.family: "Arial"
        color: graphComponent.graphColor
        text: Number(graphComponent.minValue).toFixed(0)
    }

    function addData(data) {
        // Calculate wrapped index for circular buffer
        let wrappedIndex = graphComponent.currentIndex % graphComponent.maxPoints;

        // Replace or append the new point
        if (wrappedIndex < lineSeries.count) {
            lineSeries.replace(wrappedIndex, wrappedIndex, data);
        } else {
            lineSeries.append(wrappedIndex, data);
        }

        // Increment the current index
        graphComponent.currentIndex++;
    }
}
Adding Data
To add data to the chart, simply call the addData(data) function with the new data point:

QML
graphComponent.addData(yourDataPoint);
