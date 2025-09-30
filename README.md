<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: VISHAL M S </h3>
<h3>Register Number: 212224060306 </h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
```
import random

class MedicinePrescribingAgent:
    def __init__(self):
        self.performance = 0
        self.current_room = "Room1"

    def sense(self, patient):
        """Sense the patient's temperature"""
        return patient["temperature"]

    def move(self):
        """Move agent between Room1 and Room2"""
        self.current_room = "Room2" if self.current_room == "Room1" else "Room1"
        self.performance -= 1  # movement cost
        print(f"Agent moved to {self.current_room}")

    def treat(self, patient):
        """Treat patient if unhealthy"""
        if patient["temperature"] > 98.5:
            print(f"Patient in {self.current_room} is unhealthy (Temp: {patient['temperature']}°F). Treating...")
            self.performance += 10
            patient["temperature"] = 98.5  # after treatment, set to normal
        else:
            print(f"Patient in {self.current_room} is healthy (Temp: {patient['temperature']}°F).")

    def run(self, rooms, steps=5):
        """Run the agent for a number of steps"""
        for step in range(steps):
            print(f"\n--- Step {step+1} ---")
            patient = rooms[self.current_room]
            temperature = self.sense(patient)
            self.treat(patient)
            self.move()  # move to next room

        print("\nFinal Performance Score:", self.performance)


# Environment: 2 rooms with patients
rooms = {
    "Room1": {"temperature": random.choice([97.5, 99.0, 100.2])},
    "Room2": {"temperature": random.choice([97.8, 99.5, 101.0])}
}

print("Initial Room States:", rooms)

# Create agent and run simulation
agent = MedicinePrescribingAgent()
agent.run(rooms, steps=6)```
# OUTPUT
<img width="726" height="800" alt="Screenshot 2025-09-30 104808" src="https://github.com/user-attachments/assets/8995b6fa-0259-47f3-8328-21abaed0f982" />

