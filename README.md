A Java Swing application demonstrating **MVC architecture**, **interface-based design**,  and **testing practices**.

Architecture & Design
- **MVC architecture**
- **Interface-based design**
- **Input validation and error handling**
- **SOLID principles**

Test Coverage:
- **Model tests** - temperature bounds, heating/cooling logic, state transitions
- **Controller tests** - uses mocks to verify view/model interactions in isolation

<table align="center">
  <tr>
    <td align="center" style="padding: 10px;">
      <img src="img/idle.jpg" width="300"/><br/>
      <strong>Idle</strong>
    </td>
    <td align="center" style="padding: 10px;">
      <img src="img/heating.jpg" width="300"/><br/>
      <strong>Heating</strong>
    </td>
  </tr>
  <tr>
    <td align="center" style="padding: 10px;">
      <img src="img/cooling.jpg" width="300"/><br/>
      <strong>Cooling</strong>
    </td>
    <td align="center" style="padding: 10px;">
      <img src="img/error.jpg" width="300"/><br/>
      <strong>Error</strong>
    </td>
  </tr>
</table>

## Setup

**Requirements:** Java 23 (JDK 23)

1. clone and navigate
```bash
git clone 
cd thermostat-control
```

2. compile
```bash
javac -d bin src/**/*.java
```

3. run
```bash
java -cp bin ThermostatApp
```

## Usage

**Basic Operation:**
1. Launch app → displays current temp (20°C default)
2. Enter target temp (10-35°C, 0.1° precision)
3. Click "Set Temperature"
4. System automatically heats/cools to target

**Valid Inputs:** `20`, `20.5`, `20,5` (European format)  
**Invalid:** `abc`, `50`, `20.55` (not in 0.1°C steps)

## Architecture
```
src/
├── model/
│   ├── IThermostatModel.java      # model contract
│   └── ThermostatModel.java       # business logic
├── view/
│   ├── IThermostatView.java       # view contract  
│   └── SwingThermostatView.java   # Swing GUI
├── controller/
│   ├── IThermostatController.java # controller contract
│   └── ThermostatController.java  # mediates view ↔ model
└── ThermostatApp.java             # entry point

test/
├── model/ThermostatModelTest.java      # unit tests
└── controller/ThermostatControllerTest.java  # mock tests
```
