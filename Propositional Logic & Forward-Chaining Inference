# Run: python P11_logical_inference.py
# Library: none. Only plain Python 3

# Real-world problem: Smart Home Security & Energy Control
# Rules represented as Horn Clauses: (set_of_premises, conclusion)
KNOWLEDGE_BASE = [
    ({"MotionDetected", "NightTime"}, "TurnOnLights"),
    ({"TurnOnLights", "NoOneHome"}, "IntruderAlert"),
    ({"IntruderAlert"}, "SoundAlarm"),
    ({"IntruderAlert"}, "NotifyOwner"),
    ({"TemperatureHigh", "SomeoneHome"}, "TurnOnAC")
]

def forward_chaining(facts, rules, query):
    inferred = set(facts)
    added = True
    while added:
        added = False
        for premises, conclusion in rules:
            if premises.issubset(inferred) and conclusion not in inferred:
                inferred.add(conclusion)
                print(f"Derived: {conclusion} (from {', '.join(premises)})")
                added = True
                if conclusion == query:
                    return True, inferred
    return query in inferred, inferred

if __name__ == "__main__":
    initial_facts = {"MotionDetected", "NightTime", "NoOneHome"}
    goal = "SoundAlarm"

    print(f"Initial Facts: {initial_facts}")
    print(f"Query: {goal}\n")
    proved, all_facts = forward_chaining(initial_facts, KNOWLEDGE_BASE, goal)
    print(f"\nConclusion '{goal}' Proved: {proved}")
