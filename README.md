import streamlit as st
from google import genai
client=genai.client(api_key="AQ.Ab8RN6JIF10s-XsNuzKLzZIgA71Kf_ewYK8pVqwV1gPMUep5SQ")
st.title("Email Generator")
topic=st.text_input("Enter a topic")
tone=st.selectbox("Select Tone",["Professinal","Technical","Friendly","Funny"])
length=st.slider("Length of words",500,1500,700)
if st.button("generate"):
    propmt=f"""Generate email topic topic:{topic} tone:{tone} length:{length}words
    It includes
    Subject
    Grettings
    Body
    Conclusion
    """
    response=client.models.generate_content(model="gemini-2.5-flash",contents=propmt)
    st.write(response.text)
