import streamlit as st
import pandas as pd
import numpy as np

st.set_page_config(page_title="Simple Streamlit Dashboard", layout="wide")

st.title("Simple Streamlit Dashboard")
st.subheader("Demo of interactive widgets and charts")

st.sidebar.header("Controls")

option = st.sidebar.selectbox(
    "Select data type",
    ("Random Line Data", "Random Bar Data")
)

n_points = st.sidebar.slider("Number of points", 10, 200, 50, 5)

show_table = st.sidebar.checkbox("Show data table", True)

x = np.arange(n_points)
y1 = np.random.randn(n_points).cumsum()
y2 = np.random.randn(n_points).cumsum()
y3 = np.random.randn(n_points).cumsum()

df = pd.DataFrame(
    {
        "x": x,
        "Series A": y1,
        "Series B": y2,
        "Series C": y3
    }
)

col1, col2 = st.columns([2, 1])

with col1:
    if option == "Random Line Data":
        st.markdown("### Line Chart")
        st.line_chart(df.set_index("x"))
    else:
        st.markdown("### Bar Chart")
        st.bar_chart(df[["Series A", "Series B", "Series C"]])

with col2:
    st.markdown("### Summary Statistics")
    st.write(df[["Series A", "Series B", "Series C"]].describe())

if show_table:
    st.markdown("### Raw Data")
    st.dataframe(df.reset_index(drop=True))

st.sidebar.markdown("---")
st.sidebar.write("Dashboard created with Streamlit")
