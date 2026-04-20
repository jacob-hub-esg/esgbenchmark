import { useState, useEffect } from "react";
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, ReferenceLine, ResponsiveContainer, Area, AreaChart } from "recharts";

const EMISSION_FACTORS = {
  Denmark: 0.154, Sweden: 0.045, Norway: 0.026, Finland: 0.098,
  Germany: 0.385, Netherlands: 0.283, France: 0.052, Italy: 0.233,
  Spain: 0.181, Poland: 0.635, "United Kingdom": 0.225, Belgium: 0.167,
  Lithuania: 0.216, Latvia: 0.119, Estonia: 0.471, "Czech Republic": 0.421,
  Austria: 0.104, Switzerland: 0.030, Portugal: 0.196, Greece: 0.328,
};

const EU_BENCHMARKS = {
  Office: { avg: 45, good: 28, poor: 70 },
  Residential: { avg: 35, good: 20, poor: 55 },
  Retail: { avg: 55, good: 35, poor: 85 },
  Industrial: { avg: 80, good: 50, poor: 120 },
  Hotel: { avg: 65, good: 40, poor: 100 },
  Healthcare: { avg: 90, good: 60, poor: 130 },
};

const CSRD_CHECKS = [
  { id: "scope1", label: "Scope 1 emissions tracked", weight: 20 },
  { id: "scope2", label: "Scope 2 emissions tracked", weight: 20 },
  { id: "scope3", label: "Scope 3 partial coverage", weight: 15 },
  { id: "energyAudit", label: "Energy audit conducted", weight: 15 },
  { id: "sbti", label: "SBTi target set", weight: 15 },
  { id: "thirdParty", label: "Third-party verified data", weight: 15 },
];

function getRating(value, benchmark) {
  if (value <= benchmark.good) return { label: "Excellent", color: "#22c55e", pct: 90 };
  if (value <= benchmark.avg) return { label: "Good", color: "#84cc16", pct: 70 };
  if (value <= benchmark.poor) return { label: "Average", color: "#f59e0b", pct: 45 };
  return { label: "Poor", color: "#ef4444", pct: 20 };
}

function buildDecarbPath(currentIntensity, targetYear = 2050) {
  const startYear = new Date().getFullYear();
  const years = [];
  for (let y = startYear; y <= targetYear; y++) {
    const progress = (y - startYear) / (targetYear - startYear);
    const eased = 1 - Math.pow(1 - progress, 2);
    years.push({
      year: y,
      emissions: parseFloat((currentIntensity * (1 - eased)).toFixed(2)),
      target: parseFloat((currentIntensity * (1 - ((y - startYear) / (targetYear - startYear)))).toFixed(2)),
    });
  }
  return years;
}

const CustomTooltip = ({ active, payload, label }) => {
  if (active && payload && payload.length) {
    return (
      <div style={{ background: "#0f1f1a", border: "1px solid #1a3d30", borderRadius: 8, padding: "10px 14px" }}>
        <p style={{ color: "#86efac", fontWeight: 700, margin: 0 }}>{label}</p>
        {payload.map((p, i) => (
          <p key={i} style={{ color: p.color, margin: "2px 0", fontSize: 13 }}>
            {p.name}: {p.value} kg CO₂/m²
          </p>
        ))}
      </div>
    );
  }
  return null;
};

export default function App() {
  const [step, setStep] = useState(1);
  const [form, setForm] = useState({
    country: "Denmark", buildingType: "Office", area: "", gasKwh: "", elecKwh: "", districtKwh: "",
  });
  const [csrd, setCsrd] = useState({});
  const [results, setResults] = useState(null);
  const [animIn, setAnimIn] = useState(false);

  useEffect(() => {
    setAnimIn(false);
    setTimeout(() => setAnimIn(true), 50);
  }, [step]);

  function calculate() {
    const area = parseFloat(form.area) || 1;
    const gas = parseFloat(form.gasKwh) || 0;
    const elec = parseFloat(form.elecKwh) || 0;
    const district = parseFloat(form.districtKwh) || 0;
    const ef = EMISSION_FACTORS[form.country];
    const gasEF = 0.202;
    const districtEF = 0.17;

    const scope1 = gas * gasEF;
    const scope2 = elec * ef + district * districtEF;
    const total = scope1 + scope2;
    const intensity = total / area;

    const benchmark = EU_BENCHMARKS[form.buildingType];
    const rating = getRating(intensity, benchmark);
    const csrdScore = CSRD_CHECKS.reduce((acc, c) => acc + (csrd[c.id] ? c.weight : 0), 0);
    const path = buildDecarbPath(intensity);

    setResults({ scope1, scope2, total, intensity, benchmark, rating, csrdScore, path, ef });
    setStep(4);
  }

  const inp = (field, value) => setForm(p => ({ ...p, [field]: value }));

  const s = {
    wrap: { minHeight: "100vh", background: "#071510", fontFamily: "'DM Mono', monospace", color: "#e2f5ec", padding: "0 0 60px 0" },
    header: { background: "linear-gradient(135deg, #0a2218 0%, #071510 100%)", borderBottom: "1px solid #1a3d30", padding: "28px 40px", display: "flex", alignItems: "center", gap: 16 },
    logo: { width: 36, height: 36, background: "linear-gradient(135deg, #22c55e, #16a34a)", borderRadius: 8, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18 },
    title: { fontSize: 20, fontWeight: 700, letterSpacing: "-0.5px", color: "#fff" },
    subtitle: { fontSize: 12, color: "#4ade80", letterSpacing: "2px", textTransform: "uppercase", marginTop: 2 },
    card: { background: "#0d1f18", border: "1px solid #1a3d30", borderRadius: 16, padding: 32 },
    label: { fontSize: 11, color: "#4ade80", letterSpacing: "1.5px", textTransform: "uppercase", marginBottom: 8, display: "block" },
    select: { width: "100%", background: "#071510", border: "1px solid #1a3d30", borderRadius: 8, color: "#e2f5ec", padding: "12px 14px", fontSize: 14, fontFamily: "'DM Mono', monospace", outline: "none" },
    input: { width: "100%", background: "#071510", border: "1px solid #1a3d30", borderRadius: 8, color: "#e2f5ec", padding: "12px 14px", fontSize: 14, fontFamily: "'DM Mono', monospace", outline: "none", boxSizing: "border-box" },
    btn: { background: "linear-gradient(135deg, #22c55e, #16a34a)", color: "#071510", border: "none", borderRadius: 10, padding: "14px 32px", fontSize: 14, fontWeight: 700, cursor: "pointer", fontFamily: "'DM Mono', monospace", letterSpacing: "0.5px" },
    btnOut: { background: "transparent", color: "#4ade80", border: "1px solid #1a3d30", borderRadius: 10, padding: "12px 24px", fontSize: 13, cursor: "pointer", fontFamily: "'DM Mono', monospace" },
    steps: { display: "flex", gap: 8, alignItems: "center", padding: "24px 40px" },
    stepDot: (active, done) => ({ width: 28, height: 28, borderRadius: "50%", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 12, fontWeight: 700, background: done ? "#22c55e" : active ? "#071510" : "#0d1f18", border: active ? "2px solid #22c55e" : done ? "2px solid #22c55e" : "1px solid #1a3d30", color: done ? "#071510" : active ? "#22c55e" : "#4a7a62" }),
    stepLine: { flex: 1, height: 1, background: "#1a3d30" },
  };

  const stepLabels = ["Building Info", "Energy Data", "CSRD Readiness", "Results"];

  return (
    <div style={s.wrap}>
      <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Syne:wght@700;800&display=swap" rel="stylesheet" />
      <style>{`select option { background: #071510; } input::placeholder { color: #2d5a45; } * { transition: border-color 0.2s; } select:focus, input:focus { border-color: #22c55e !important; } .fade-in { animation: fadeUp 0.4s ease forwards; } @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }`}</style>

      <div style={s.header}>
        <div style={s.logo}>🌿</div>
        <div>
          <div style={{ ...s.title, fontFamily: "'Syne', sans-serif" }}>BuildingCarbon.io</div>
          <div style={s.subtitle}>Emissions Benchmark & Decarbonisation Tool</div>
        </div>
        <div style={{ marginLeft: "auto", fontSize: 11, color: "#2d5a45", letterSpacing: "1px" }}>POWERED BY GHG PROTOCOL</div>
      </div>

      <div style={s.steps}>
        {stepLabels.map((l, i) => (
          <>
            <div style={{ display: "flex", flexDirection: "column", alignItems: "center", gap: 6 }}>
              <div style={s.stepDot(step === i + 1, step > i + 1)}>{step > i + 1 ? "✓" : i + 1}</div>
              <span style={{ fontSize: 10, color: step === i + 1 ? "#4ade80" : "#2d5a45", letterSpacing: "1px" }}>{l.toUpperCase()}</span>
            </div>
            {i < 3 && <div style={s.stepLine} />}
          </>
        ))}
      </div>

      <div style={{ maxWidth: 760, margin: "0 auto", padding: "0 24px" }} className={animIn ? "fade-in" : ""}>

        {step === 1 && (
          <div style={s.card}>
            <h2 style={{ fontFamily: "'Syne', sans-serif", fontSize: 24, margin: "0 0 6px", color: "#fff" }}>Building Information</h2>
            <p style={{ color: "#4a7a62", fontSize: 13, margin: "0 0 32px" }}>Tell us about your property so we can benchmark accurately.</p>
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 24, marginBottom: 24 }}>
              <div>
                <label style={s.label}>Country</label>
                <select style={s.select} value={form.country} onChange={e => inp("country", e.target.value)}>
                  {Object.keys(EMISSION_FACTORS).sort().map(c => <option key={c}>{c}</option>)}
                </select>
              </div>
              <div>
                <label style={s.label}>Building Type</label>
                <select style={s.select} value={form.buildingType} onChange={e => inp("buildingType", e.target.value)}>
                  {Object.keys(EU_BENCHMARKS).map(t => <option key={t}>{t}</option>)}
                </select>
              </div>
            </div>
            <div style={{ marginBottom: 32 }}>
              <label style={s.label}>Total Floor Area (m²)</label>
              <input style={s.input} type="number" placeholder="e.g. 2500" value={form.area} onChange={e => inp("area", e.target.value)} />
            </div>
            <div style={{ display: "flex", justifyContent: "flex-end" }}>
              <button style={{ ...s.btn, opacity: form.area ? 1 : 0.5 }} onClick={() => form.area && setStep(2)}>Next →</button>
            </div>
          </div>
        )}

        {step === 2 && (
          <div style={s.card}>
            <h2 style={{ fontFamily: "'Syne', sans-serif", fontSize: 24, margin: "0 0 6px", color: "#fff" }}>Annual Energy Consumption</h2>
            <p style={{ color: "#4a7a62", fontSize: 13, margin: "0 0 8px" }}>Enter annual kWh for each energy source. Leave blank if not applicable.</p>
            <div style={{ background: "#071510", border: "1px solid #1a3d30", borderRadius: 8, padding: "10px 16px", marginBottom: 28, fontSize: 12, color: "#4ade80" }}>
              📍 Grid emission factor for <strong>{form.country}</strong>: <strong>{EMISSION_FACTORS[form.country]} kg CO₂/kWh</strong>
            </div>
            {[
              { key: "gasKwh", label: "Natural Gas (Scope 1)", placeholder: "e.g. 45000", factor: "0.202 kg CO₂/kWh" },
              { key: "elecKwh", label: "Electricity (Scope 2)", placeholder: "e.g. 120000", factor: `${EMISSION_FACTORS[form.country]} kg CO₂/kWh` },
              { key: "districtKwh", label: "District Heating (Scope 2)", placeholder: "e.g. 30000", factor: "0.17 kg CO₂/kWh" },
            ].map(f => (
              <div key={f.key} style={{ marginBottom: 20 }}>
                <label style={s.label}>{f.label}</label>
                <div style={{ position: "relative" }}>
                  <input style={s.input} type="number" placeholder={f.placeholder} value={form[f.key]} onChange={e => inp(f.key, e.target.value)} />
                  <span style={{ position: "absolute", right: 14, top: "50%", transform: "translateY(-50%)", fontSize: 11, color: "#2d5a45" }}>{f.factor}</span>
                </div>
              </div>
            ))}
            <div style={{ display: "flex", justifyContent: "space-between", marginTop: 32 }}>
              <button style={s.btnOut} onClick={() => setStep(1)}>← Back</button>
              <button style={s.btn} onClick={() => setStep(3)}>Next →</button>
            </div>
          </div>
        )}

        {step === 3 && (
          <div style={s.card}>
            <h2 style={{ fontFamily: "'Syne', sans-serif", fontSize: 24, margin: "0 0 6px", color: "#fff" }}>CSRD Readiness Check</h2>
            <p style={{ color: "#4a7a62", fontSize: 13, margin: "0 0 28px" }}>Which sustainability practices does your organisation currently have in place?</p>
            {CSRD_CHECKS.map(c => (
              <div key={c.id} onClick={() => setCsrd(p => ({ ...p, [c.id]: !p[c.id] }))}
                style={{ display: "flex", alignItems: "center", gap: 14, padding: "14px 18px", borderRadius: 10, marginBottom: 10, cursor: "pointer", background: csrd[c.id] ? "#0a2218" : "#071510", border: `1px solid ${csrd[c.id] ? "#22c55e" : "#1a3d30"}` }}>
                <div style={{ width: 22, height: 22, borderRadius: 6, background: csrd[c.id] ? "#22c55e" : "transparent", border: `2px solid ${csrd[c.id] ? "#22c55e" : "#1a3d30"}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 13, color: "#071510", flexShrink: 0 }}>
                  {csrd[c.id] ? "✓" : ""}
                </div>
                <span style={{ fontSize: 13, flex: 1 }}>{c.label}</span>
                <span style={{ fontSize: 11, color: "#4a7a62" }}>+{c.weight}pts</span>
              </div>
            ))}
            <div style={{ display: "flex", justifyContent: "space-between", marginTop: 32 }}>
              <button style={s.btnOut} onClick={() => setStep(2)}>← Back</button>
              <button style={s.btn} onClick={calculate}>Calculate Emissions →</button>
            </div>
          </div>
        )}

        {step === 4 && results && (
          <div>
            {/* Summary Cards */}
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 16, marginBottom: 20 }}>
              {[
                { label: "Total Emissions", value: results.total.toFixed(0), unit: "kg CO₂e/yr", color: "#f59e0b" },
                { label: "Emission Intensity", value: results.intensity.toFixed(1), unit: "kg CO₂/m²", color: results.rating.color },
                { label: "CSRD Score", value: results.csrdScore, unit: "/ 100 pts", color: results.csrdScore >= 70 ? "#22c55e" : results.csrdScore >= 40 ? "#f59e0b" : "#ef4444" },
              ].map(m => (
                <div key={m.label} style={{ ...s.card, padding: 24, textAlign: "center" }}>
                  <div style={{ fontSize: 11, color: "#4a7a62", letterSpacing: "1.5px", textTransform: "uppercase", marginBottom: 10 }}>{m.label}</div>
                  <div style={{ fontSize: 32, fontWeight: 700, fontFamily: "'Syne', sans-serif", color: m.color }}>{m.value.toLocaleString()}</div>
                  <div style={{ fontSize: 12, color: "#4a7a62", marginTop: 4 }}>{m.unit}</div>
                </div>
              ))}
            </div>

            {/* Benchmark */}
            <div style={{ ...s.card, marginBottom: 20 }}>
              <h3 style={{ fontFamily: "'Syne', sans-serif", margin: "0 0 20px", color: "#fff" }}>EU Benchmark — {form.buildingType} Buildings</h3>
              <div style={{ display: "flex", alignItems: "center", gap: 12, marginBottom: 16 }}>
                <span style={{ fontSize: 11, color: "#4a7a62", width: 60 }}>Your building</span>
                <div style={{ flex: 1, background: "#071510", borderRadius: 99, height: 12, overflow: "hidden", border: "1px solid #1a3d30" }}>
                  <div style={{ width: `${Math.min(100, (results.intensity / (results.benchmark.poor * 1.3)) * 100)}%`, height: "100%", background: results.rating.color, borderRadius: 99, transition: "width 1s ease" }} />
                </div>
                <span style={{ fontSize: 14, fontWeight: 700, color: results.rating.color, width: 80, textAlign: "right" }}>{results.intensity.toFixed(1)} kg/m²</span>
              </div>
              {[
                { label: "Best-in-class", value: results.benchmark.good, color: "#22c55e" },
                { label: "EU Average", value: results.benchmark.avg, color: "#4ade80" },
                { label: "Poor performers", value: results.benchmark.poor, color: "#ef4444" },
              ].map(b => (
                <div key={b.label} style={{ display: "flex", alignItems: "center", gap: 12, marginBottom: 8 }}>
                  <span style={{ fontSize: 11, color: "#4a7a62", width: 100 }}>{b.label}</span>
                  <div style={{ flex: 1, background: "#071510", borderRadius: 99, height: 6, overflow: "hidden", border: "1px solid #1a3d30" }}>
                    <div style={{ width: `${Math.min(100, (b.value / (results.benchmark.poor * 1.3)) * 100)}%`, height: "100%", background: b.color, opacity: 0.4, borderRadius: 99 }} />
                  </div>
                  <span style={{ fontSize: 12, color: b.color, width: 80, textAlign: "right" }}>{b.value} kg/m²</span>
                </div>
              ))}
              <div style={{ marginTop: 20, padding: "14px 18px", borderRadius: 10, background: "#071510", border: `1px solid ${results.rating.color}`, display: "flex", alignItems: "center", gap: 12 }}>
                <div style={{ width: 10, height: 10, borderRadius: "50%", background: results.rating.color, flexShrink: 0 }} />
                <span style={{ fontSize: 13 }}>Your building rates <strong style={{ color: results.rating.color }}>{results.rating.label}</strong> compared to EU peers in the {form.buildingType.toLowerCase()} sector.</span>
              </div>
            </div>

            {/* Scope Breakdown */}
            <div style={{ ...s.card, marginBottom: 20 }}>
              <h3 style={{ fontFamily: "'Syne', sans-serif", margin: "0 0 20px", color: "#fff" }}>Scope Breakdown</h3>
              <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 16 }}>
                {[
                  { label: "Scope 1 — Direct (Gas)", value: results.scope1, note: "Natural gas combustion on-site" },
                  { label: "Scope 2 — Indirect (Grid)", value: results.scope2, note: "Purchased electricity & district heat" },
                ].map(sc => (
                  <div key={sc.label} style={{ background: "#071510", borderRadius: 10, padding: 20, border: "1px solid #1a3d30" }}>
                    <div style={{ fontSize: 11, color: "#4a7a62", letterSpacing: "1px", textTransform: "uppercase", marginBottom: 8 }}>{sc.label}</div>
                    <div style={{ fontSize: 26, fontWeight: 700, fontFamily: "'Syne', sans-serif", color: "#fff" }}>{sc.value.toFixed(0).toLocaleString()}</div>
                    <div style={{ fontSize: 11, color: "#4a7a62", marginTop: 4 }}>kg CO₂e/yr</div>
                    <div style={{ marginTop: 12, height: 4, borderRadius: 99, background: "#1a3d30" }}>
                      <div style={{ width: `${(sc.value / results.total) * 100}%`, height: "100%", background: "#22c55e", borderRadius: 99 }} />
                    </div>
                    <div style={{ fontSize: 11, color: "#4ade80", marginTop: 6 }}>{((sc.value / results.total) * 100).toFixed(0)}% of total</div>
                    <div style={{ fontSize: 11, color: "#2d5a45", marginTop: 4 }}>{sc.note}</div>
                  </div>
                ))}
              </div>
            </div>

            {/* Decarbonisation Path */}
            <div style={{ ...s.card, marginBottom: 20 }}>
              <h3 style={{ fontFamily: "'Syne', sans-serif", margin: "0 0 4px", color: "#fff" }}>Decarbonisation Pathway to Net Zero 2050</h3>
              <p style={{ color: "#4a7a62", fontSize: 12, margin: "0 0 24px" }}>Projected trajectory from current intensity to net zero using an accelerated reduction curve.</p>
              <ResponsiveContainer width="100%" height={220}>
                <AreaChart data={results.path} margin={{ top: 5, right: 20, left: 0, bottom: 5 }}>
                  <defs>
                    <linearGradient id="emGrad" x1="0" y1="0" x2="0" y2="1">
                      <stop offset="5%" stopColor="#22c55e" stopOpacity={0.2} />
                      <stop offset="95%" stopColor="#22c55e" stopOpacity={0} />
                    </linearGradient>
                  </defs>
                  <CartesianGrid strokeDasharray="3 3" stroke="#1a3d30" />
                  <XAxis dataKey="year" tick={{ fill: "#4a7a62", fontSize: 11 }} tickLine={false} interval={4} />
                  <YAxis tick={{ fill: "#4a7a62", fontSize: 11 }} tickLine={false} axisLine={false} unit=" kg" />
                  <Tooltip content={<CustomTooltip />} />
                  <ReferenceLine y={0} stroke="#22c55e" strokeDasharray="4 4" label={{ value: "Net Zero", fill: "#22c55e", fontSize: 11 }} />
                  <Area type="monotone" dataKey="emissions" stroke="#22c55e" strokeWidth={2.5} fill="url(#emGrad)" name="Your trajectory" dot={false} />
                  <Line type="monotone" dataKey="target" stroke="#4a7a62" strokeWidth={1.5} strokeDasharray="5 5" name="Linear target" dot={false} />
                </AreaChart>
              </ResponsiveContainer>
              <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12, marginTop: 16 }}>
                {[
                  { year: 2030, reduction: "43%" },
                  { year: 2040, reduction: "72%" },
                  { year: 2050, reduction: "100%" },
                ].map(m => (
                  <div key={m.year} style={{ background: "#071510", borderRadius: 8, padding: "12px 16px", border: "1px solid #1a3d30", textAlign: "center" }}>
                    <div style={{ fontSize: 11, color: "#4a7a62", marginBottom: 4 }}>{m.year} Target</div>
                    <div style={{ fontSize: 20, fontWeight: 700, fontFamily: "'Syne', sans-serif", color: "#22c55e" }}>{m.reduction}</div>
                    <div style={{ fontSize: 10, color: "#2d5a45" }}>reduction</div>
                  </div>
                ))}
              </div>
            </div>

            {/* CSRD Score */}
            <div style={{ ...s.card, marginBottom: 20 }}>
              <h3 style={{ fontFamily: "'Syne', sans-serif", margin: "0 0 20px", color: "#fff" }}>CSRD Readiness Score</h3>
              <div style={{ display: "flex", alignItems: "center", gap: 24, marginBottom: 24 }}>
                <div style={{ width: 90, height: 90, borderRadius: "50%", background: `conic-gradient(${results.csrdScore >= 70 ? "#22c55e" : results.csrdScore >= 40 ? "#f59e0b" : "#ef4444"} ${results.csrdScore * 3.6}deg, #071510 0deg)`, display: "flex", alignItems: "center", justifyContent: "center", flexShrink: 0 }}>
                  <div style={{ width: 68, height: 68, borderRadius: "50%", background: "#0d1f18", display: "flex", alignItems: "center", justifyContent: "center" }}>
                    <span style={{ fontSize: 22, fontWeight: 700, fontFamily: "'Syne', sans-serif", color: results.csrdScore >= 70 ? "#22c55e" : results.csrdScore >= 40 ? "#f59e0b" : "#ef4444" }}>{results.csrdScore}</span>
                  </div>
                </div>
                <div>
                  <div style={{ fontSize: 16, fontWeight: 700, color: "#fff", marginBottom: 6 }}>
                    {results.csrdScore >= 70 ? "CSRD Ready" : results.csrdScore >= 40 ? "Partially Ready" : "Action Required"}
                  </div>
                  <div style={{ fontSize: 13, color: "#4a7a62", lineHeight: 1.6 }}>
                    {results.csrdScore >= 70 ? "Your organisation demonstrates strong sustainability governance." : results.csrdScore >= 40 ? "Several key practices are in place, but gaps remain before full CSRD compliance." : "Significant groundwork is needed to meet CSRD reporting requirements."}
                  </div>
                </div>
              </div>
              <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 8 }}>
                {CSRD_CHECKS.map(c => (
                  <div key={c.id} style={{ display: "flex", alignItems: "center", gap: 10, padding: "8px 12px", borderRadius: 8, background: "#071510", border: `1px solid ${csrd[c.id] ? "#22c55e33" : "#1a3d30"}` }}>
                    <span style={{ fontSize: 14 }}>{csrd[c.id] ? "✅" : "⬜"}</span>
                    <span style={{ fontSize: 12, color: csrd[c.id] ? "#e2f5ec" : "#4a7a62" }}>{c.label}</span>
                  </div>
                ))}
              </div>
            </div>

            <div style={{ display: "flex", justifyContent: "center" }}>
              <button style={s.btnOut} onClick={() => { setStep(1); setForm({ country: "Denmark", buildingType: "Office", area: "", gasKwh: "", elecKwh: "", districtKwh: "" }); setCsrd({}); setResults(null); }}>
                ↩ Start New Assessment
              </button>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}
