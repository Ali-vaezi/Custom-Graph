# **QML Graph Component**  

A lightweight and customizable **graph/chart UI component** for **Qt applications** using **QML and QtCharts**. This component allows you to visualize real-time data efficiently.  

## **📌 Features**  

- 📈 **Customizable line graph** with color, scaling, and transparency options.  
- 🔄 **Efficient real-time data updates** using a circular buffer approach.  
- 🎨 **Fully customizable UI**, including axis visibility, colors, and margins.  
- ⚡ **Optimized performance** for smooth graph rendering.  
- 📉 **Adjustable data range**, including min/max values and blank spaces.  

## **🚀 Getting Started**  

### **1️⃣ Add the QML File to Your Project**  

Copy the `CustomGraph2.qml` file into your Qt project.  

### **2️⃣ Import Required Modules**  

Ensure you have the required Qt modules in your `main.qml` or any relevant QML file:  

```qml
import QtQuick 2.15
import QtCharts 2.15
```

### **3️⃣ Use the Component in Your QML File**  

Add the **CustomGraph2** to your QML project:  

```qml
CustomGraph2 {
    id: myGraph
    width: 800
    height: 300
    graphColor: "#ff0000"  // Customize graph color
    maxPoints: 500         // Set maximum data points
    minValue: 0
    maxValue: 200
}
```

### **4️⃣ Add Data to the Graph**

Dynamically update the graph by calling the **addData()** function:

```qml
myGraph.addData(150)  // Adds a new data point to the graph
```

## **📌 Example Use Cases**

📊 Real-time data visualization (e.g., sensor readings, live signals, performance metrics).

📡 Network monitoring applications (e.g., bandwidth, latency graphs).

🏥 Medical devices displaying heart rate, pulse, or oxygen levels.

