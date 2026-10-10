# MRA-Ai-Studio

import streamlit as st

st.set_page_config(
    page_title="Razzaq AI Studio",
    page_icon="✨",
    layout="centered"
)

st.title("✨ MRA AI Studio")
st.write("Free CV Maker & Social Media Post Maker")

tool = st.selectbox(
    "Choose your tool",
    ["CV Maker", "Social Media Post Maker"]
)

if tool == "CV Maker":
    st.subheader("Create your CV")

    name = st.text_input("Full name")
    phone = st.text_input("Phone number")
    city = st.text_input("City")
    education = st.text_input("Education")
    skills = st.text_input("Skills")
    experience = st.text_area("Work experience")
    target_job = st.text_input("Job title")

    if st.button("Generate CV", type="primary"):
        if not name or not target_job:
            st.warning("Please enter your name and job title.")
        else:
            cv = f"""
{name.upper()}
{phone}
{city}

PROFESSIONAL PROFILE
Candidate applying for {target_job}.

EDUCATION
{education}

SKILLS
{skills}

WORK EXPERIENCE
{experience}
"""
            st.text_area("Your CV draft", cv, height=300)
            st.download_button(
                "Download CV draft",
                data=cv,
                file_name="my_cv.txt",
                mime="text/plain"
            )

else:
    st.subheader("Create a social media post")

    business = st.text_input("Business name")
    service = st.text_input("Product or service")
    offer = st.text_input("Price or offer")
    contact = st.text_input("Contact details")
    language = st.selectbox(
        "Language",
        ["English", "Roman Urdu"]
    )

    if st.button("Generate Post", type="primary"):
        if not business or not service:
            st.warning("Enter your business name and service.")
        else:
            if language == "Roman Urdu":
                post = (
                    f"{business}\n\n"
                    f"{service} ab hasil karein!\n"
                    f"{offer}\n\n"
                    f"Order ke liye rabta karein: {contact}"
                )
            else:
                post = (
                    f"{business}\n\n"
                    f"Looking for {service}?\n"
                    f"{offer}\n\n"
                    f"Contact us: {contact}"
                )

            st.markdown("### Post preview")
            st.info(post)
            st.download_button(
                "Download post text",
                data=post,
                file_name="social_post.txt",
                mime="text/plain"
            )
