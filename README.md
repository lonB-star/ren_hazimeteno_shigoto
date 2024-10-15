# ren_hazimeteno_shigoto

import pandas as pd

csv_path = input("csv_path>>")
trans_path = csv_path.replace("\\", "/").strip("'").strip('"')

with open(trans_path, mode='r', encoding='ANSI', errors='replace') as f:
    data = pd.read_csv(f)

for index, row in data.iterrows():
    print("-----------------------------------------------")
    for col in data.columns:
        if pd.isna(row[col]):
            new_vaue = input(f"{col}>>")
            data.at[index, col] = new_vaue

            data.to_csv(csv_path, mode='w', index=False, encoding='ANSI')
        else:
            print(f"{col}: {row[col]}")
