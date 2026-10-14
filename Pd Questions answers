import streamlit as st
from google import genai

# Page Config
st.set_page_config(page_title="स्त्री-आरोग्य AI सखी", page_icon="🌸", layout="centered")

# Header Section
st.title("🌸 स्त्री-आरोग्य AI सखी")
st.subheader("मासिक पाळी आणि आरोग्याविषयीच्या तुमच्या प्रश्नांची उत्तरे मिळवा")

# Disclaimer (महत्त्वाची सूचना)
st.warning(
    "⚠️ **टीप:** हा ॲप केवळ माहिती आणि जागरूकतेसाठी आहे. गंभीर त्रास असल्यास किंवा वैद्यकीय उपचारांसाठी कृपया डॉक्टरांचा सल्ला नक्की घ्या."
)

# API Key Input
api_key = st.text_input("तुमची Google Gemini API Key प्रविष्ट करा:", type="password")

if api_key:
    client = genai.Client(api_key=api_key)

    # User Input Form
    user_question = st.text_area(
        "तुमचा प्रश्न इथे लिहा (उदा. मासिक पाळीत पोट दुखत असल्यास काय करावे?):",
        height=100
    )

    if st.button("उत्तर मिळवा 🌸"):
        if user_question.strip() != "":
            with st.spinner("तुमच्या प्रश्नाचे उत्तर तयार केले जात आहे..."):
                try:
                    prompt = f"""
                    तुम्ही एक अत्यंत संवेदनशील, सहानुभूतीपूर्वक आणि तज्ज्ञ महिला आरोग्य सल्लागार (Gynecologist) आहात.
                    मुलींच्या किंवा महिलांच्या मासिक पाळी (Periods), हायजीन, आणि आरोग्याविषयी विचारलेल्या प्रश्नाचे उत्तर द्या.
                    
                    अटी:
                    १. उत्तर सोप्या, स्पष्ट आणि आदरयुक्त मराठी भाषेत असावे.
                    २. उत्तर वाचून भीती वाटणार नाही अशा सकारात्मक भाषेत लिहा.
                    ३. आवश्यक असल्यास घरगुती सोपे उपाय सांगा.
                    ४. शेवटी डॉक्टरांचा सल्ला कधी घ्यावा याचे मार्गदर्शन करा.
                    
                    प्रश्न: {user_question}
                    """

                    response = client.models.generate_content(
                        model='gemini-2.5-flash',
                        contents=prompt,
                    )

                    st.markdown("---")
                    st.success("### 💬 एआय सखीचे उत्तर:")
                    st.write(response.text)

                except Exception as e:
                    st.error(f"काहीतरी अडचण आली: {e}")
        else:
            st.warning("कृपया आधी तुमचा प्रश्न टाइप करा.")
else:
    st.info("👈 ॲप सुरू करण्यासाठी कृपया तुमची
