KAVALI EV CHARGING INTELLIGENCE — UPGRADE V3

Files:
- app.py: upgraded Streamlit application
- requirements.txt: Python dependencies

What changed:
1. Simulated EV queue is stored in Streamlit session state, so a new EV is not lost after st.rerun().
2. Duplicate EV IDs are rejected; a reset button restores the queue from the source CSV.
3. Adds per-EV deadline diagnostics: required average power before deadline, individual charger-limit feasibility, and a caution status.
4. Click effects are off by default to reduce visual clutter in the sidebar.
5. UI wording avoids claiming real-time telemetry.

Run in the existing project folder:
1. Back up your current app.py.
2. Copy this app.py into the folder containing your Kavali CSV files.
3. Activate your existing .venv.
4. Run: python -m streamlit run app.py

Expected data files:
- kavali_ev_clean_hourly_forecast.csv (or the synthetic hourly CSV configured in the app)
- kavali_ev_stations.csv
- the EV request CSV configured by the app (optional; the app handles a missing file)

Notes:
- The Kavali data is synthetic. Do not present its forecasts as measured real-world demand.
- Forecast-aware headroom is an estimate, not live meter data.
- Deadline diagnostics flag individual feasibility; they do not guarantee a schedule when EVs share station capacity.
- Python syntax compilation and an optimizer smoke test passed in the build environment. The full Streamlit UI was not launched in this build environment; run locally to validate against your data files.
