# DataCleaning

```py
import pandas as pd
# Define a function to clean the data
def clean_data(df):
    # Drop missing values if less than 5% are missing
    if df.isna().mean().mean() < 0.05:
        df.dropna(inplace=True)
    else:
        # Allow user to choose a fill method
        fill_method = st.radio("Choose a fill method:", ['mean', 'median', 'mode'])
        if fill_method == 'mean':
            df.fillna(df.mean(), inplace=True)
        elif fill_method == 'median':
            df.fillna(df.median(), inplace=True)
        else:
            df.fillna(df.mode(), inplace=True)

    # Drop duplicates and outliers
    df.drop_duplicates(inplace=True)
    df = df[(df - df.mean()).abs() < 3 * df.std()]

    return df

```
