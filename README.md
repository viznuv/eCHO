```markdown
# Echo Chamber Dynamics in AI-Human Conversations

This repository contains a Python simulation model that demonstrates echo chamber effects in one-on-one conversations between a human and an AI. The simulation incorporates influence parameters, political views (e.g., conservative vs. liberal), and tolerance scales for both agents. It is designed to explore how repeated, tailored interactions can drive opinion polarization.

## Overview

In this simulation, opinions are represented as continuous values in the range **[-1, 1]**, where:
- **-1** represents an extreme liberal view.
- **1** represents an extreme conservative view.

### Agents

- **HumanAgent**  
  - **Initial Opinion:** The human starts with an initial opinion (e.g., a moderate liberal view of -0.2).
  - **Tolerance:** The human accepts AI responses only if they are within a specified tolerance.
  - **Influence (μ):** The human updates their opinion gradually by shifting a fraction of the difference toward the AI's response.

- **AIAgent**  
  - **Fixed Political Leaning (`ai_view`):** The AI has an inherent political bias (e.g., a strongly conservative view of 0.8).
  - **Tolerance (`ai_tolerance`):** If the human's opinion is close enough to the AI’s view (within `ai_tolerance`), the AI echoes by reinforcing the human’s stance. Otherwise, it pulls the opinion toward its own view.
  - **Reinforcement Factors:**  
    - **Echo (`beta_echo`):** When the human's opinion is similar to the AI's view.
    - **Pull (`beta_pull`):** When the human's opinion deviates significantly.
  - **Noise (`σ`):** A small noise is added to the AI's response to mimic variability.

### Conversation Dynamics

The simulation runs for a fixed number of conversation turns (`T`). In each turn:
1. **Human Posting:** The human posts their current opinion.
2. **AI Response:** The AI generates a response based on the human's opinion and its own political bias.
3. **Opinion Update:** The human evaluates the AI response and, if it falls within their tolerance, updates their opinion accordingly.

The evolution of both the human's opinion and the AI's responses are recorded and visualized, illustrating how echo chamber effects can develop over time.

## Requirements

- Python 3.x
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)

You can install the required packages using pip:

```bash
pip install numpy matplotlib
```

## Usage

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/echo-chamber-dynamics.git
   cd echo-chamber-dynamics
   ```

2. **Run the Simulation:**

   ```bash
   python conversation_model.py
   ```

   This command will execute the simulation and display plots showing the evolution of the human’s opinion alongside the AI’s responses.

## Configuration

The simulation parameters can be modified directly in the `conversation_model.py` file. Key parameters include:

- **HumanAgent Parameters:**
  - `initial_opinion`: Starting opinion (e.g., -0.2 for a moderate liberal stance).
  - `human_tolerance`: Maximum acceptable difference for updating opinion.
  - `mu`: Influence (learning rate) determining the extent of opinion update.

- **AIAgent Parameters:**
  - `ai_view`: The inherent political leaning of the AI (e.g., 0.8 for conservative).
  - `ai_tolerance`: Tolerance for echoing versus pulling behavior.
  - `beta_echo`: Reinforcement factor when the human's opinion is close to the AI's view.
  - `beta_pull`: Pulling factor when the human's opinion is far from the AI's view.
  - `sigma`: Noise level in the AI's response.

- **Conversation Parameter:**
  - `T`: Number of conversation turns.

Adjust these parameters to simulate various scenarios, such as when the AI's bias strongly contrasts with the human's view, or when the human is more or less receptive to influence.

## Output

When you run the simulation, two key visualizations are generated:
1. **Opinion Evolution Plot:**  
   Displays the human’s opinion (blue line) and the AI responses (red markers) over the conversation turns.
2. **(Optional) Difference Analysis:**  
   You can extend the code to plot the difference between the AI response and the human opinion to further analyze the interaction dynamics.

## Project Structure

```
echo-chamber-dynamics/
├── conversation_model.py      # Main simulation code
├── README.md                  # This file
└── requirements.txt           # (Optional) List of required packages
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

This simulation is inspired by research on echo chamber dynamics in social networks, particularly the work by Kazutoshi Sasahara. It is intended as a simplified framework for exploring how tailored AI-human interactions can contribute to opinion polarization.

