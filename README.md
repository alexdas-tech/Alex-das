import streamlit as st
import random

# --- APP CONFIGURATION ---
st.set_page_config(page_title="Bharat Cash Coach", page_icon="💰", layout="centered")

# --- PREMIUM CUSTOM STYLING (CSS) ---
st.markdown("""
    <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
    
    html, body, [class*="css"] { font-family: 'Inter', sans-serif; }
    
    .main { background-color: #0E1117; }
    
    /* Premium Card Design */
    .earning-card {
        background: linear-gradient(145deg, #1e1e26, #14141b);
        border-radius: 15px;
        padding: 20px;
        margin-bottom: 20px;
        border-left: 5px solid #FFD700; /* Gold Border for Premium feel */
        box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    }
    
    .premium-card {
        background: linear-gradient(145deg, #1a2a1a, #0d150d);
        border-left: 5px solid #2ecc71; /* Emerald for Paid/Growth ideas */
    }

    .urgent-badge {
        background-color: #e74c3c;
        color: white;
        padding: 2px 8px;
        border-radius: 5px;
        font-size: 0.8rem;
        font-weight: bold;
    }

    .stButton>button {
        width: 100%;
        border-radius: 12px;
        height: 3.5em;
        background: linear-gradient(to right, #FFD700, #FFA500);
        color: #000;
        font-weight: bold;
        border: none;
        transition: 0.3s;
    }
    
    .stButton>button:hover {
        transform: scale(1.02);
        box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
    }
    </style>
    """, unsafe_allow_html=True)

# --- HEADER ---
st.title("💰 Bharat Cash Coach")
st.caption("Expert Daily Income Strategies for India • Version 2026.4")

# --- INPUT AREA ---
col1, col2 = st.columns(2)
with col1:
    user_status = st.selectbox("Your Status", ["Free Member", "Premium Member ⭐"])
with col2:
    target_amount = st.text_input("Amount Goal (e.g. ₹500)", value="₹500")

# --- ACTION BUTTONS ---
btn_col1, btn_col2 = st.columns(2)
with btn_col1:
    urgent_trigger = st.button("🚨 I NEED MONEY TODAY")
with btn_col2:
    daily_trigger = st.button("📅 DAILY UNIQUE IDEA")

# --- LOGIC ENGINE ---

def show_card(title, why, steps, time, earning, diff, is_premium=False):
    css_class = "earning-card premium-card" if is_premium else "earning-card"
    steps_html = "".join([f"<li>{s}</li>" for s in steps])
    
    st.markdown(f"""
    <div class="{css_class}">
        <h3 style="margin-top:0; color:#FFD700;">{title}</h3>
        <p><b>Why it works:</b> {why}</p>
        <ul style="padding-left:20px;">{steps_html}</ul>
        <div style="display: flex; justify-content: space-between; font-size: 0.9rem; color: #bbb;">
            <span>⏳ {time}</span>
            <span>💵 {earning}</span>
            <span>📊 {diff}</span>
        </div>
    </div>
    """, unsafe_allow_html=True)

# --- EXECUTION ---

# 1. URGENT MODE
if urgent_trigger:
    st.header("⚡ Fast Cash (Next 24 Hours)")
    show_card(
        "Hyperlocal UPI Runner",
        "Elderly neighbors often need medicine or groceries but avoid delivery apps due to high fees.",
        ["Post in your society/mohalla WhatsApp: 'Doing a pharmacy/milk run at 6PM. Only ₹30 fee.'", 
         "Collect 5-10 small orders.", 
         "Deliver and collect cash/UPI instantly."],
        "2 Hours", "₹200 - ₹400", "Easy"
    )
    show_card(
        "Digital Storefront Auditor",
        "Local shops have wrong timings on Google Maps. You fix them for a quick tip.",
        ["Find a local shop with 'Closed' or 'Missing' info on Maps.", 
         "Show the owner and offer to update it + add 3 fresh photos.", 
         "Ask for ₹100 for the 5-minute 'SEO update'."],
        "1 Hour", "₹100 - ₹300", "Easy"
    )
    show_card(
        "Used Book Liquidator",
        "Second-hand markets (like Daryaganj or local stalls) buy college books instantly.",
        ["Gather 3-5 unused textbooks or bestsellers.", 
         "Take them to a local second-hand dealer.", 
         "Negotiate and get UPI/Cash on the spot."],
        "3 Hours", "₹300 - ₹800", "Medium"
    )

# 2. PREMIUM MODE
elif user_status == "Premium Member ⭐":
    st.header("💎 High-Scale Earning Methods")
    # Idea 1: AI Specialist
    show_card(
        "WhatsApp AI Chatbot Mediator",
        "Small boutiques need auto-replies for pricing. You set this up using 'AutoResponder for WA'.",
        ["Identify a boutique/Instagram seller with slow replies.", 
         "Use AI to draft 10 common FAQs.", 
         "Setup the free auto-responder app on their phone. Charge a setup fee + monthly 'maintenance'."],
        "4 Hours Setup", "₹2,000 - ₹5,000 / month", "Medium", True
    )
    # Idea 2: Scalable Content
    show_card(
        "Hyperlocal Newsletter Curator",
        "People want to know 'What's happening in [Your Area] this weekend?'",
        ["Start a WhatsApp Channel for your suburb.", 
         "Curate weekend deals, park events, and new cafe openings.", 
         "Once you hit 500 followers, charge local cafes ₹500 for a shoutout."],
        "Daily 1 hour", "Scales to ₹10k+", "Medium", True
    )
    st.info("💡 Pro Tip: Use Canva for all visuals to keep the brand look 'High-End'.")

# 3. DAILY IDEA
elif daily_trigger:
    show_card(
        "The 'Status' Salesman",
        "Small home-bakers have no reach. You act as their affiliate.",
        ["Find a local home-baker and ask for their menu photos.", 
         "Post on your WhatsApp status: 'Ordering from here, let me know if you want to club orders for free delivery.'", 
         "Ask the baker for a ₹50 'referral' for every new customer you bring."],
        "30 Mins", "₹150 - ₹300", "Easy"
    )

# 4. NORMAL MODE (Default)
else:
    if st.button("Show 3 Fresh Ideas"):
        show_card(
            "Reel-to-Menu Designer",
            "Cafes have physical menus but no 'video' menus for Instagram.",
            ["Record 5-second clips of a cafe's top 3 dishes.", 
             "Use a free app (CapCut/VN) to make a 15-sec Reel with trending audio.", 
             "Sell the Reel to the owner for their Instagram page."],
            "2 Hours", "₹300 - ₹500", "Medium"
        )
        show_card(
            "Tech-Tutor for Seniors",
            "Grandparents want to use DigiLocker or book train tickets but are scared.",
            ["Offer a 1-hour 'Safety First' tech session in your colony.", 
             "Teach them how to use UPI safely and block spam.", 
             "Charge a respectful ₹200 per session."],
            "1 Hour", "₹200", "Easy"
        )
        show_card(
            "Bulk-Laundry Middleman",
            "Local 'Dhobis' are cheap but don't offer pick-up. You bridge the gap.",
            ["Offer pick-up/drop service for laundry in your building.", 
             "Bundle 5 neighbors' clothes, take them to the Dhobi.", 
             "Charge ₹50 service fee per household."],
            "2 Hours", "₹250", "Easy"
        )

# --- FOOTER ---
st.divider()
st.caption("⚠️ SAFE EARNING GUARANTEE: No gambling, scams, or risky trading. All methods are 100% ethical.")
