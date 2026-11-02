import numpy as np
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import learning_curve
from sklearn.datasets import load_iris

# 1. Load Dataset
X, y = load_iris(return_X_y=True)

# 2. Evaluasi Learning Curve untuk max_depth Berbeda
for depth in [1, 4, None]:
    model = DecisionTreeClassifier(max_depth=depth, random_state=42)
    
    train_sizes, train_scores, val_scores = learning_curve(
        model, X, y, cv=5, train_sizes=np.linspace(0.1, 1.0, 6)
    )
    
    print(f"max_depth={depth}: train={train_scores.mean():.3f}, val={val_scores.mean():.3f}")
