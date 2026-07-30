import streamlit as st
import streamlit.components.v1 as components

# 1. Configure Web Page Layout
st.set_page_config(
    page_title="AMN Sniper Dashboard",
    layout="wide",
    initial_sidebar_state="expanded"
)

st.title("🦅 AMN Sniper Analysis Dashboard")
st.caption("Live TradingView Integration & Strategy Confluence Matrix")

# 2. Create a Two-Column Interface (Chart on Left, Rules/Analysis on Right)
col1, col2 = st.columns([3, 1.2])

with col1:
    st.subheader("Live Market Feed")
    
    # Advanced TradingView Technical Widget HTML Embed
    tradingview_html = """
    <div class="tradingview-widget-container" style="height:100%;width:100%;">
        <div id="tradingview_chart"></div>
        <script type="text/javascript" src="https://tradingview.com"></script>
        <script type="text/javascript">
        new TradingView.widget({
            "autosize": true,
            "symbol": "FX_IDC:XAUUSD",
            "interval": "5",
            "timezone": "Etc/UTC",
            "theme": "dark",
            "style": "1",
            "locale": "en",
            "toolbar_bg": "#f1f3f6",
            "enable_publishing": false,
            "hide_side_toolbar": false,
            "allow_symbol_change": true,
            "container_id": "tradingview_chart"
        });
        </script>
    </div>
    """
    # Render the chart at 650px height
    components.html(tradingview_html, height=650)

with col2:
    st.subheader("AMN Strategy Matrix")
    st.markdown("---")
    
    # Interactive Input Section for Manual Metrics
    st.markdown("### 1. Structural Bias")
    bias = st.radio("Current Market Direction:", ("Bullish (Demand)", "Bearish (Supply)", "Consolidating"))
    
    st.markdown("### 2. AMN Entry Checklist")
    cond_1 = st.checkbox("Liquidity Sweep / Stop Hunt executed?")
    cond_2 = st.checkbox("Market Structure Shift (MSS) confirmed on 5M/1M?")
    cond_3 = st.checkbox("Price tapped into premium/discount FVG?")
    cond_4 = st.checkbox("Displacement candle showing strong momentum?")
    
    # 3. Dynamic Automated Trade Assessment Engine
    st.markdown("### 3. Execution Signal")
    confluences_met = sum([cond_1, cond_2, cond_3, cond_4])
    
    if confluences_met == 4:
        st.success(f"🔥 HIGH PROBABILITY ENTRY: All 4 confluences aligned for a {bias} trade!")
    elif confluences_met == 3:
        st.warning(f"⚠️ MODERATE RISK: 3/4 confluences met. Wait for final confirmation.")
    else:
        st.error(f"❌ NO TRADE: Only {confluences_met}/4 requirements satisfied. Exercise patience.")
        
    st.markdown("---"
