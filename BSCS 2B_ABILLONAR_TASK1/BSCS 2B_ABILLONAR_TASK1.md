PART 1 — Pre-Lab Concept Questions (15 minutes) Answer the following before running the simulation:
1.	What is an agent in an Agent-Based Model? 
An agent in Agent-Based Model is an individual unit in the simulation that can make decisions and act based on a set of rules. Agents can represent people, animals, vehicles, or other objects in a system. Each agent can interact with other agents and with the environment around it. These interactions and behaviors help the model show how complex patterns or changes happen in the whole system.

2.	What is the difference between:
•	global variables
•	species variables? 
The difference between global variables and species variables is how they are used in a model. Global variables are shared by the whole model and can be used by all agents and parts of the simulation. They store information that affects the entire system. Species variables, on the other hand, belong to a specific type of agent (species). Each agent of that species has its own value for that variable. For example, a global variable could be the total population, while species variable could be the age or speed of each agent.

3.	What does this expression mean? student mean_of each.attention 
The expression student mean_of each.attention means calculating the average attention level of all students. It takes the attention value of every student agent and then finds the mean (average) of those values. This helps show the overall attention level of the student group in the model.

4.	What happens if attention continuously decreases without a break?
If attention continuously decreases without a break, the students’ attention level will keep getting lower over time. Eventually, their attention may reach a very low level or even zero. This means the students in the model would become very distracted or stop paying attention completely, which can affect the overall results of the simulation.

PART 2 — Run the Base Model
![alt text](image-1.png)

![alt text](image-2.png)

Observe:
• Does attention collapse?
• Does performance still improve?
Explain why.
When you change the decay rate to 0.05, the students lose their focus very quickly. This causes the average attention to collapse toward zero almost immediately after a break ends. The new decay rate is much faster than the old rate of 0.02. Now, students lose focus just as fast as they gain it during their rest time. Because of this, the performance will not improve or it will grow very slowly. Student agents usually need a high level of focus to do their schoolwork well. Since their attention is always crashing, they do not have enough focus to finish their tasks. The system becomes very difficult for the students to succeed in. This change shows that losing focus too quickly prevents any real learning from happening.

Activity 3: Performance Growth Condition
![alt text](image-3.png)

Questions:
• Does performance improve slower?
Yes. Performance will improve much slower. Before, students only needed 60% attention to learn, which is easier to reach. Now, they must reach 80% attention. Because students spend less time at this very high level of focus, they have fewer chances to increase their performance score.
• What does this represent in real classroom settings?
In a real classroom, this represents a more difficult subject or a stricter grading system. It means that just "paying a little attention" is not enough to succeed. Students must be "highly focused" or "deeply engaged" to actually understand the lesson and get better grades. If the lesson is too hard, many students might not reach that high level of focus, and their performance will stay low.

PART 3 — Data Observation Table
![alt text](image-4.png)

PART 4 — Guided Code Analysis
![alt text](image-5.png)

Questions:
1.	Does attention increase faster?
No. Attention does not increase faster. Because the breaks happen more often (every 15 cycles), the students are interrupted frequently. They do not have enough time to focus deeply before the next break starts.

2.	Does performance grow faster?
No. Performance grows slower. Since there are more breaks, there is less time for "actual work." The students spend more time resting and less time finishing their tasks compared to the 30-cycle version.

3.	Is the system more stable?
Yes. The system is more stable. Instead of big "ups and downs" in attention, the frequent breaks keep the levels more even. The graph will look flatter because the changes are smaller and more balanced.

Activity 2: Attention Decay Rate
Original:
attention <- max(0.0, attention - 0.02);
Task:
Change decay rate to:
0.05
![alt text](image-9.png)
Observe:
• Does attention collapse?
    The attention level collapses because students are losing their focus more than twice as fast as before. Because this decay rate is now equal to the recovery rate, the students lose all the focus they gained during a break almost immediately once class starts again.
• Does performance still improve?
    Performance will stop improving or will grow very slowly. Student agents generally need to maintain a certain level of focus to complete tasks, since their attention crashes to zero so quickly, they no longer have the required "brainpower" to increase their performance scores.
Explain why.

PART 5 — Experiment: Class Size Impact (30 minutes) 
![alt text](image-6.png), ![alt text](image-8.png)

Analysis Questions:
1. Does increasing class size affect average attention?
    No. In this simulation, each student agent follows the same individual rule for attention regardless of how many other students are in the room. Because there is no "distraction" logic built into the code to make students affect one another, the average attention remains stable even when you increase the class size from 10 to 100 students.
2. Does mobility create more randomness?
    Yes. When students are stationary, their behavior is very predictable. However, when you add mobility, each student moves to a new, random location in every cycle. This makes the classroom map look more chaotic, as the distribution of student colors (which represent attention levels) shifts constantly.
3. Is emergent behavior visible?
    Yes. Even though every student follows the exact same simple rule for attention, you will see complex patterns appear that you did not specifically program. You might notice "clusters" of students forming, where groups of green (focused) or red (unfocused) students move together. This is a classic example of emergent behavior, where simple individual actions create a larger, unpredictable pattern in the whole system.

PART 6 — Data Analysis Task (Optional Python)
Using Excel or Power Query Editor
1. Load classroom_data.csv
2. Plot:
o Attention vs Cycle
o Performance vs Cycle
![alt text](image-7.png)
Interpretation: This graph will show you how attention rises and falls over time and how performance gradually climbs in response.
3. Identifying Break Cycles
    The simulation data reveals a clear relationship between the is_break status and the avg_attention levels. During cycles marked as TRUE (break periods), the avg_attention consistently increases, indicating that students are recovering their focus. Conversely, when the status is FALSE (working periods), the avg_attention exhibits a steady decline, reflecting the attention decay rate programmed into the model. This creates a distinct 'sawtooth' pattern in the data, confirming that regular breaks are essential for maintaining student attention levels over time.
4. Compute correlation between attention and performance.
    The correlation between average attention and average performance is about -0.02. In simple terms, this means there is no direct connection between how focused the students are at one specific moment and how much their performance changes at that same moment. Attention is what helps students reach a higher grade, but the performance score itself acts as a permanent record of what they have already learned. Because of this, the two numbers do not move up and down together at the same time.
Question:
Is performance strongly dependent on attention?
Performance is conditionally dependent on attention. It requires high levels of focus to increase, but it is not directly tied to temporary shifts in attention. Students only climb to a higher performance level when their attention is high enough to earn those points. Once they reach a new level, they stay there even if their attention drops later. Because performance is a record of what has already been learned, it remains stable even when focus dips. This explains why the two numbers do not move up and down together at the same time.

PART 7 — Critical Thinking Questions
1. Why does performance only increase when attention > 0.6?
    This value serves as a cognitive threshold. The simulation assumes that learning cannot occur unless a student is sufficiently engaged. By setting the threshold at 0.6, the model gates performance gains so that they only register during periods of adequate focus, preventing the system from attributing learning to times when the student is distracted.
2. Is this model deterministic or stochastic?
    The model is stochastic. In a deterministic model, the same inputs would always yield identical results. Because this simulation includes probabilistic elements, such as random student movement or random fluctuations in attention levels, it produces different outcomes across multiple runs.
3. What real-world classroom factors are missing?
    The model is too simple because it leaves out many real-world factors. It does not include a teacher to manage the class, ignore outside distractions like noise, or show how different students learn at different speeds. Also, it assumes students never forget what they have learned, which does not happen in a real classroom.
4. How would peer influence affect the system?
    Adding peer influence would change how students act in the classroom. Instead of working alone, students would start to affect each other. If a student is near someone who is distracted, they might become distracted too. This creates a "contagion" effect where groups of students start acting the same way at the same time. This turns individual behavior into a collective pattern where focus or distraction spreads through the whole room.

PART 8 — Advanced Extension Tasks (Choose One)
Option A: Peer Influence
Add logic:
• Students near high-attention peers increase attention.

Code:
reflex peer_influence {
        // Look for students within a radius of 10
        list<student> neighbors <- student at_distance 10.0;
        
        if (length(neighbors) > 0) {
            float avg_neighbor_attention <- neighbors mean_of each.attention;
            
            // Adjust attention based on neighbors
            if (avg_neighbor_attention > 0.7) {
                attention <- min(1.0, attention + 0.02);
            } else if (avg_neighbor_attention < 0.4) {
                attention <- max(0.0, attention - 0.02);
            }
        }
    }


This addition introduces a social interaction mechanism to the simulation to better represent classroom dynamics.

How the Logic Works:

Neighborhood Search: Each student agent scans for other students within a 10-meter radius.

Calculation: The agent calculates the average attention level of these neighbors.

Social Effect: If the average neighbor attention is above 0.7, the student's attention increases. If the average is below 0.4, the student's attention decreases.

Impact on the Simulation:
By adding this rule, the simulation moves from independent behavior to social dynamics. This creates a "contagion" effect where focus or distraction spreads through the room. Instead of acting alone, students now form clusters where groups either work hard or become distracted in tandem, mirroring how peer influence functions in a real classroom environment.

Conclusion:
This simulation shows that classroom performance is a dynamic system influenced by social interaction. By using agent-based modeling, it becomes clear how simple rules, like maintaining focus, lead to large-scale patterns.

The addition of peer influence highlights the contagion effect, where focus or distraction spreads through groups rather than occurring in isolation. These results confirm that a classroom environment is sensitive to the behavior of neighboring peers. Ultimately, this model explains how social dynamics impact overall learning outcomes.


