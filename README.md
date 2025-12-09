# Feature Scaling-Standardization


Feature scaling is a crucial step in the data preprocessing phase of machine learning. It involves transforming the features of your dataset to ensure that they are on a similar scale. This is particularly important for algorithms that rely on distance calculations, such as k-nearest neighbors and support vector machines.

## Standardization

Standardization, also known as Z-score normalization, is a common method of feature scaling. It transforms the data such that the features have a mean of 0 and a standard deviation of 1. The formula for standardization is:

```z = (x - μ) / σ
```
Where:
- `z` is the standardized value
- `x` is the original value
- `μ` is the mean of the feature
- `σ` is the standard deviation of the feature

## Implementation in Python

    from sklearn.model_selection import train_test_split
    
    x_train, x_test, y_train, y_test = train_test_split(
    df.drop('Purchased', axis=1),
    df['Purchased'],
    test_size=0.3,
    random_state=0
    )
    from sklearn.preprocessing import StandardScaler

    scaler = StandardScaler()
    
    x_train_scaled = scaler.fit_transform(x_train)
    x_test_scaled = scaler.transform(x_test)


    from sklearn.linear_model import LogisticRegression

    lr = LogisticRegression()
    lr_scale = LogisticRegression()
    
    lr.fit(x_train, y_train)
    lr_scale.fit(x_train_scaled, y_train)
    
    y_pred = lr.predict(x_test)
    y_pred_scaled = lr_scale.predict(x_test_scaled)

    from sklearn.metrics import accuracy_score

    print("Actual:", accuracy_score(y_test, y_pred))
    print("Scaled:", accuracy_score(y_test, y_pred_scaled))
## Conclusion
Standardization is an effective technique for feature scaling that can improve the performance of machine learning algorithms. By ensuring that all features are on a similar scale, models can converge faster and achieve better accuracy. Always consider applying feature scaling as part of your data preprocessing pipeline.

## when to use Standardization

Standardization is particularly useful when:
- The features have different units or scales.
- The algorithm assumes a Gaussian distribution of the data (e.g., linear regression, logistic regression).
- You are using distance-based algorithms 
        - k-nearest neighbors
        - Support vector machines
        - Principal Component Analysis (PCA)
        -Artificial Neural Networks
        -k-means
- etc..


