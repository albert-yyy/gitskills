import pandas as pd
import csv
import tkinter as tk
from tkinter import filedialog


def getLocalFile():
    root = tk.Tk()
    root.withdraw()

    filePath = filedialog.askopenfilename()
    print('文件路径：', filePath)

    return filePath


target_path = getLocalFile()


df_bean_activity = pd.read_csv('kl_law_bean_activity.csv')
df_bean_activity.columns = ['id', 'code', 'name', 'num', 'type', 'a', 'b', 'c']
dict_bean_activity = df_bean_activity.set_index('name')['code'].to_dict()
# print(df_bean_activity.head())
# print(dict_bean_activity)

df_bean = pd.read_excel(target_path, dtype=str)
# print(df_bean.head())
name = df_bean.columns[2]   # 发给我excel里对应功能名称
if ('扣除' in name) or ('结算' in name):  # 1获得  3扣除
    activity_type = '3'
elif '添加' in name:
    activity_type = '1'

if '咨询' in name:     # 律豆类目 2词条 3咨询 4交易宝 5线索中心
    category = '3'    # 咨询
elif '词条' in name:
    category = '2'    # 词条


result = []
# for index, row in df_bean.iterrows():
#     result.append(row['手机号'] + '||' + dict_bean_activity[name]
#                   + '||' + activity_type + '||' + row[name] + '||'
#                   + '||' + category + '||' + row['日期']
#                   )
# print(result[0])

with open('{}.csv'.format(target_path), 'w', newline='') as f:
        writer = csv.writer(f)
        for index, row in df_bean.iterrows():
            writer.writerow([row['手机号'] + '||' + dict_bean_activity[name]
                          + '||' + activity_type + '||' + row[name] + '||'
                          + category + '||' + row['日期']
                          ])
