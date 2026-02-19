# Quick Start

## Example: Find wells with cement bond logs

Python:

import pandas as pd
df = pd.read_csv("volve_catalog_master.csv")
df[df["tags"].str.contains("CBL", na=False)]["well"].unique()

## Example: Find DLIS logs for a well

df[(df["well"]=="15/9-F-11B") & (df["ext_norm"]=="dlis")]

## Example: Find drilling reports

df[df["tags"].str.contains("DDR", na=False)]
