from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, roc_auc_score
from imblearn.over_sampling import SMOTE
import joblib

# Load preprocessed data
X_train, X_test, y_train, y_test = load_data()

# Handle class imbalance with SMOTE
smote = SMOTE(random_state=42)
X_res, y_res = smote.fit_resample(X_train, y_train)

# Train Random Forest
model = RandomForestClassifier(
    n_estimators=100,
    max_depth=10,
    class_weight='balanced'
)
model.fit(X_res, y_res)

# Evaluate
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))
joblib.dump(model, 'models/fraud_detector.pkl')
