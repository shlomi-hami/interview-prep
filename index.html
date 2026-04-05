import { useState } from "react";

const SYSTEM_PROMPT = `אתה עוזר מקצועי של שלומי חמי, מטפל טבעי ומדקר עם מעל 20 שנות ניסיון. הקליניקה נקראת Therapoint בכפר סבא. שלומי מתמחה בדיקורתופדי — שיטה המשלבת טיפול פיזי עם עבודה רגשית ותת-מודעת. הפרויקט נקרא "גב אל גב". הקהל: אנשים שסובלים מכאבי גב, צוואר ואגן, גילאי 30-65, מחפשים פתרון טבעי.

שלומי מנהל ראיון כמוביל שיחה — לא מראיין פסיבי, לא דומיננטי לגמרי. הוא שואל שאלות חדות, מביע דעה משלו, ומחבר בין עולם האורח לעולם שלו.

קבל פרטי מרואיין ומטרות הראיון, והחזר JSON בלבד ללא backticks:

{
  "title_options": ["כותרת אפשרות 1", "כותרת אפשרות 2", "כותרת אפשרות 3"],
  "thumbnail_text": "טקסט לתאמבנייל עד 6 מילים",
  "pre_call_script": "סקריפט מפורט לשיחה המקדימה — מה שלומי אומר, שואל ומבקש. כולל: פתיחה חמה, הסבר על הפרויקט והקהל, תיאום ציפיות לגבי הראיון, שאלות להכרת המרואיין לעומק, ובקשות ספציפיות (תמונה, אישור פרסום, ציוד טכני). כתוב כשיחה אמיתית, לא רשימה.",
  "pre_call_requests": ["בקשה ספציפית 1 שצריך לבקש ממנה", "בקשה 2", "בקשה 3"],
  "opening": "פתיחה מומלצת לראיון עצמו — מה שלומי אומר בהתחלה (2-3 משפטים)",
  "outline": [
    {"segment": "שם הסגמנט", "duration": "X דקות", "goal": "מטרת הסגמנט", "questions": ["שאלה 1", "שאלה 2", "שאלה 3"]},
    {"segment": "שם הסגמנט", "duration": "X דקות", "goal": "מטרת הסגמנט", "questions": ["שאלה 1", "שאלה 2"]},
    {"segment": "שם הסגמנט", "duration": "X דקות", "goal": "מטרת הסגמנט", "questions": ["שאלה 1", "שאלה 2"]},
    {"segment": "שם הסגמנט", "duration": "X דקות", "goal": "מטרת הסגמנט", "questions": ["שאלה 1", "שאלה 2"]},
    {"segment": "סיום", "duration": "2-3 דקות", "goal": "סגירה חזקה", "questions": ["שאלה סיום 1"]}
  ],
  "shlomi_angles": ["זווית / נקודת מבט שלומי 1 — איפה הוא יכול להוסיף דעה", "זווית 2", "זווית 3"],
  "caution_points": ["נקודת זהירות 1 — מה לא לעשות בראיון הזה", "נקודת זהירות 2"],
  "closing_note": "הערה אחרונה — מה הכי חשוב שיצא מהראיון הזה"
}`;

const STEPS = [
  { id: "guest", title: "פרטי האורח", icon: "👤" },
  { id: "topic", title: "נושא ומטרות", icon: "🎯" },
  { id: "context", title: "הקשר נוסף", icon: "📋" },
];

const inputStyle = {
  width: "100%",
  background: "#f8f6f1",
  border: "2px solid #e8e0d0",
  borderRadius: "10px",
  padding: "12px 16px",
  color: "#2a1f0e",
  fontSize: "14px",
  outline: "none",
  boxSizing: "border-box",
  fontFamily: "inherit",
  transition: "border-color 0.2s",
};

const labelStyle = {
  display: "block",
  color: "#8a7055",
  fontSize: "12px",
  fontWeight: 700,
  marginBottom: "6px",
  letterSpacing: "0.8px",
  textTransform: "uppercase",
};

export default function InterviewPrep() {
  const [step, setStep] = useState(0);
  const [form, setForm] = useState({
    name: "", title: "", expertise: "", bio: "",
    topic: "", angle: "", audience_specific: "סובלים מכאבי גב כרוניים",
    goal_primary: "", goal_secondary: "", duration: "45", format: "זום", notes: "",
  });
  const [checkedItems, setCheckedItems] = useState({});
  const [customItems, setCustomItems] = useState([]);
  const [newItemText, setNewItemText] = useState("");
  const [loading, setLoading] = useState(false);
  const [result, setResult] = useState(null);
  const [activeSection, setActiveSection] = useState("precall");
  const [copied, setCopied] = useState("");
  const [error, setError] = useState("");
  const [archive, setArchive] = useState([]);
  const [showArchive, setShowArchive] = useState(false);

  // Load archive from storage on mount
  useState(() => {
    (async () => {
      try {
        const saved = await window.storage.get("interview_archive");
        if (saved?.value) setArchive(JSON.parse(saved.value));
      } catch {}
    })();
  });

  const saveToArchive = async (resultData, formData) => {
    const entry = {
      id: Date.now(),
      date: new Date().toLocaleDateString("he-IL"),
      name: formData.name,
      topic: formData.topic,
      form: formData,
      result: resultData,
    };
    const updated = [entry, ...archive].slice(0, 20);
    setArchive(updated);
    try {
      await window.storage.set("interview_archive", JSON.stringify(updated));
    } catch {}
    return updated;
  };

  const loadFromArchive = (entry) => {
    setForm(entry.form);
    setResult(entry.result);
    setCheckedItems({});
    setCustomItems([]);
    setShowArchive(false);
    setActiveSection("precall");
  };

  const deleteFromArchive = async (id) => {
    const updated = archive.filter(e => e.id !== id);
    setArchive(updated);
    try {
      await window.storage.set("interview_archive", JSON.stringify(updated));
    } catch {}
  };

  const update = (k, v) => setForm(f => ({ ...f, [k]: v }));

  const generate = async () => {
    setLoading(true);
    setError("");
    setResult(null);

    const prompt = `פרטי המרואיין:
שם: ${form.name}
תפקיד / תואר: ${form.title}
תחום התמחות: ${form.expertise}
רקע קצר: ${form.bio}

נושא הראיון: ${form.topic}
זווית / גישה: ${form.angle}
קהל יעד ספציפי: ${form.audience_specific === "אחר" ? (form.audience_other || "לא צוין") : form.audience_specific}
מטרה עיקרית: ${form.goal_primary}
מטרה משנית: ${form.goal_secondary}
משך הראיון המתוכנן: ${form.duration} דקות
פורמט: ${form.format === "אחר" ? (form.format_other || "לא צוין") : form.format}
הערות נוספות: ${form.notes || "אין"}

החזר JSON בלבד.`;

    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-5",
          max_tokens: 4000,
          system: SYSTEM_PROMPT,
          messages: [{ role: "user", content: prompt }],
        }),
      });

      if (!res.ok) {
        const e = await res.json();
        throw new Error(e?.error?.message || `HTTP ${res.status}`);
      }

      const data = await res.json();
      const text = data.content?.map(b => b.text || "").join("") || "";
      const clean = text.replace(/```json|```/g, "").trim();
      const parsed = JSON.parse(clean);
      setResult(parsed);
      await saveToArchive(parsed, form);
      setActiveSection("precall");
    } catch (e) {
      setError(`שגיאה: ${e.message}`);
    } finally {
      setLoading(false);
    }
  };

  const copy = (text, key) => {
    navigator.clipboard.writeText(text);
    setCopied(key);
    setTimeout(() => setCopied(""), 2000);
  };

  const CopyBtn = ({ text, id }) => (
    <button onClick={() => copy(text, id)} style={{
      background: copied === id ? "#5a7a3a" : "transparent",
      color: copied === id ? "#fff" : "#b09070",
      border: `1px solid ${copied === id ? "#5a7a3a" : "#d8c8a8"}`,
      borderRadius: "6px", padding: "3px 10px", fontSize: "11px",
      cursor: "pointer", fontFamily: "inherit", transition: "all 0.2s",
    }}>
      {copied === id ? "✓" : "העתק"}
    </button>
  );

  const canProceed = () => {
    if (step === 0) return form.name && form.expertise;
    if (step === 1) return form.topic && form.goal_primary;
    return true;
  };

  const SECTIONS = [
    { id: "precall", label: "📞 שיחה מקדימה" },
    { id: "checklist", label: "✅ צ'ק ליסט" },
    { id: "outline", label: "📐 מבנה הראיון" },
    { id: "titles", label: "✍️ כותרות" },
    { id: "angles", label: "💡 הזוויות שלי" },
    { id: "caution", label: "⚠️ דגשים" },
  ];

  return (
    <div style={{
      minHeight: "100vh",
      background: "linear-gradient(160deg, #faf7f2 0%, #f0e8d8 100%)",
      fontFamily: "'Georgia', 'Times New Roman', serif",
      direction: "rtl",
      padding: "32px 16px",
    }}>
      <div style={{ maxWidth: "740px", margin: "0 auto" }}>

        {/* Header */}
        <div style={{ textAlign: "center", marginBottom: "36px" }}>
          <div style={{ fontSize: "11px", color: "#b09070", letterSpacing: "4px", marginBottom: "10px" }}>
            גב אל גב • THERAPOINT
          </div>
          <h1 style={{ fontSize: "28px", fontWeight: 700, color: "#2a1f0e", margin: "0 0 6px 0", letterSpacing: "-0.5px" }}>
            הכנה לראיון
          </h1>
          <p style={{ color: "#9a8060", fontSize: "14px", margin: "0 0 14px 0", fontStyle: "italic" }}>
            מלא את הפרטים — קבל את כל ההכנה לראיון
          </p>
          {archive.length > 0 && (
            <button onClick={() => setShowArchive(!showArchive)} style={{
              background: showArchive ? "#8a6030" : "transparent",
              color: showArchive ? "#fff" : "#8a6030",
              border: "1.5px solid #8a6030", borderRadius: "8px",
              padding: "7px 18px", fontSize: "12px", fontWeight: 700,
              cursor: "pointer", fontFamily: "sans-serif",
            }}>
              📁 ארכיון ראיונות ({archive.length})
            </button>
          )}
        </div>

        {/* Archive panel */}
        {showArchive && (
          <div style={{
            background: "#fff", border: "1px solid #e8dcc8", borderRadius: "14px",
            padding: "20px", marginBottom: "24px",
            boxShadow: "0 4px 24px rgba(139,96,48,0.06)",
          }}>
            <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "14px", fontFamily: "sans-serif" }}>
              ראיונות שמורים
            </div>
            {archive.map(entry => (
              <div key={entry.id} style={{
                display: "flex", justifyContent: "space-between", alignItems: "center",
                padding: "12px 14px", borderRadius: "10px", marginBottom: "8px",
                background: "#f8f4ee", border: "1px solid #e8dcc8",
              }}>
                <div style={{ flex: 1 }}>
                  <div style={{ fontWeight: 700, color: "#2a1f0e", fontSize: "14px" }}>{entry.name}</div>
                  <div style={{ fontSize: "12px", color: "#9a8060", fontFamily: "sans-serif", marginTop: "2px" }}>
                    {entry.topic} • {entry.date}
                  </div>
                </div>
                <div style={{ display: "flex", gap: "8px" }}>
                  <button onClick={() => loadFromArchive(entry)} style={{
                    background: "#8a6030", color: "#fff", border: "none",
                    borderRadius: "7px", padding: "6px 14px", fontSize: "12px",
                    cursor: "pointer", fontFamily: "sans-serif", fontWeight: 600,
                  }}>פתח</button>
                  <button onClick={() => deleteFromArchive(entry.id)} style={{
                    background: "transparent", color: "#c8a878", border: "1px solid #e8dcc8",
                    borderRadius: "7px", padding: "6px 10px", fontSize: "13px",
                    cursor: "pointer", fontFamily: "sans-serif",
                  }}>×</button>
                </div>
              </div>
            ))}
          </div>
        )}

        {!result ? (
          <>
            {/* Step indicator */}
            <div style={{ display: "flex", justifyContent: "center", gap: "8px", marginBottom: "28px" }}>
              {STEPS.map((s, i) => (
                <div key={s.id} style={{ display: "flex", alignItems: "center", gap: "8px" }}>
                  <div style={{
                    width: "32px", height: "32px", borderRadius: "50%",
                    background: i <= step ? "#8a6030" : "#e8dcc8",
                    color: i <= step ? "#fff" : "#b09070",
                    display: "flex", alignItems: "center", justifyContent: "center",
                    fontSize: "13px", fontWeight: 700, transition: "all 0.3s",
                    fontFamily: "sans-serif",
                  }}>
                    {i < step ? "✓" : i + 1}
                  </div>
                  <span style={{ fontSize: "12px", color: i === step ? "#2a1f0e" : "#b09070", fontFamily: "sans-serif" }}>
                    {s.title}
                  </span>
                  {i < STEPS.length - 1 && <div style={{ width: "24px", height: "1px", background: "#d8c8a8" }} />}
                </div>
              ))}
            </div>

            {/* Form card */}
            <div style={{
              background: "#fff",
              border: "1px solid #e8dcc8",
              borderRadius: "16px",
              padding: "28px",
              marginBottom: "20px",
              boxShadow: "0 4px 24px rgba(139,96,48,0.06)",
            }}>
              {step === 0 && (
                <div style={{ display: "grid", gap: "18px" }}>
                  <div>
                    <label style={labelStyle}>שם המרואיין/ת *</label>
                    <input value={form.name} onChange={e => update("name", e.target.value)}
                      placeholder="שם מלא" style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>תפקיד / תואר</label>
                    <input value={form.title} onChange={e => update("title", e.target.value)}
                      placeholder='למשל: "מטפלת ברפואת תדרים, מוסמכת ב..."' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>תחום התמחות *</label>
                    <input value={form.expertise} onChange={e => update("expertise", e.target.value)}
                      placeholder='למשל: "רפואת תדרים — קולנים טיפוליים"' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>רקע קצר (אופציונלי)</label>
                    <textarea value={form.bio} onChange={e => update("bio", e.target.value)}
                      placeholder="כמה משפטים על הרקע, הניסיון, מה מייחד אותה"
                      style={{ ...inputStyle, minHeight: "80px", resize: "vertical" }} />
                  </div>
                </div>
              )}

              {step === 1 && (
                <div style={{ display: "grid", gap: "18px" }}>
                  <div>
                    <label style={labelStyle}>נושא הראיון *</label>
                    <input value={form.topic} onChange={e => update("topic", e.target.value)}
                      placeholder='למשל: "האם קולנים יכולים לעזור לכאב כרוני?"' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>זווית / גישה</label>
                    <input value={form.angle} onChange={e => update("angle", e.target.value)}
                      placeholder='למשל: "בין ספקן מסקרן לפתוח לחלוטין"' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>מטרה עיקרית של הראיון *</label>
                    <input value={form.goal_primary} onChange={e => update("goal_primary", e.target.value)}
                      placeholder='למשל: "לתת לקהל כלי מעשי חדש לכאב"' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>מטרה משנית</label>
                    <input value={form.goal_secondary} onChange={e => update("goal_secondary", e.target.value)}
                      placeholder='למשל: "לחזק את הסמכות שלי כמי שמביא תוכן מגוון"' style={inputStyle} />
                  </div>
                  <div>
                    <label style={labelStyle}>קהל יעד ספציפי</label>
                    <select value={form.audience_specific} onChange={e => update("audience_specific", e.target.value)}
                      style={{ ...inputStyle, cursor: "pointer" }}>
                      <option value="סובלים מכאבי גב כרוניים">סובלים מכאבי גב כרוניים</option>
                      <option value="אחר">אחר</option>
                    </select>
                    {form.audience_specific === "אחר" && (
                      <input value={form.audience_other || ""} onChange={e => update("audience_other", e.target.value)}
                        placeholder="תאר את הקהל הספציפי" style={{ ...inputStyle, marginTop: "8px" }} />
                    )}
                  </div>
                </div>
              )}

              {step === 2 && (
                <div style={{ display: "grid", gap: "18px" }}>
                  <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: "14px" }}>
                    <div>
                      <label style={labelStyle}>משך הראיון (דקות)</label>
                      <input value={form.duration} onChange={e => update("duration", e.target.value)}
                        placeholder="45" style={inputStyle} type="number" />
                    </div>
                    <div>
                      <label style={labelStyle}>פורמט</label>
                      <select value={form.format} onChange={e => update("format", e.target.value)}
                        style={{ ...inputStyle, cursor: "pointer" }}>
                        <option value="זום">זום</option>
                        <option value="אחר">אחר</option>
                      </select>
                      {form.format === "אחר" && (
                        <input value={form.format_other || ""} onChange={e => update("format_other", e.target.value)}
                          placeholder="תאר את הפורמט" style={{ ...inputStyle, marginTop: "8px" }} />
                      )}
                    </div>
                  </div>
                  <div>
                    <label style={labelStyle}>הערות נוספות</label>
                    <textarea value={form.notes} onChange={e => update("notes", e.target.value)}
                      placeholder="כל מה שחשוב לדעת — רגישויות, הסכמות מראש, נושאים לא לגעת בהם"
                      style={{ ...inputStyle, minHeight: "100px", resize: "vertical" }} />
                  </div>
                </div>
              )}
            </div>

            {/* Navigation */}
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center" }}>
              {step > 0 ? (
                <button onClick={() => setStep(s => s - 1)} style={{
                  background: "transparent", color: "#9a8060", border: "1px solid #d8c8a8",
                  borderRadius: "10px", padding: "12px 24px", fontSize: "14px",
                  cursor: "pointer", fontFamily: "inherit",
                }}>
                  ← חזור
                </button>
              ) : <div />}

              {step < STEPS.length - 1 ? (
                <button onClick={() => setStep(s => s + 1)} disabled={!canProceed()} style={{
                  background: canProceed() ? "#8a6030" : "#e8dcc8",
                  color: canProceed() ? "#fff" : "#b09070",
                  border: "none", borderRadius: "10px", padding: "12px 28px",
                  fontSize: "14px", fontWeight: 700, cursor: canProceed() ? "pointer" : "not-allowed",
                  fontFamily: "inherit", transition: "all 0.2s",
                }}>
                  המשך ←
                </button>
              ) : (
                <button onClick={generate} disabled={loading} style={{
                  background: loading ? "#e8dcc8" : "linear-gradient(135deg, #8a6030, #b08040)",
                  color: loading ? "#b09070" : "#fff",
                  border: "none", borderRadius: "10px", padding: "14px 32px",
                  fontSize: "15px", fontWeight: 700, cursor: loading ? "not-allowed" : "pointer",
                  fontFamily: "inherit", boxShadow: loading ? "none" : "0 4px 16px rgba(139,96,48,0.3)",
                }}>
                  {loading ? "⏳ מכין את הראיון..." : "✦ צור הכנה לראיון"}
                </button>
              )}
            </div>

            {error && <div style={{ color: "#c0392b", textAlign: "center", marginTop: "16px", fontSize: "13px", fontFamily: "sans-serif" }}>{error}</div>}
          </>
        ) : (
          <div style={{ animation: "fadeIn 0.4s ease" }}>

            {/* Guest header */}
            <div style={{
              background: "#fff", border: "1px solid #e8dcc8", borderRadius: "14px",
              padding: "20px 24px", marginBottom: "20px",
              boxShadow: "0 4px 24px rgba(139,96,48,0.06)",
            }}>
              <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                <div>
                  <div style={{ fontSize: "20px", fontWeight: 700, color: "#2a1f0e", marginBottom: "4px" }}>
                    {form.name}
                  </div>
                  <div style={{ fontSize: "13px", color: "#9a8060", fontStyle: "italic" }}>{form.title}</div>
                  <div style={{ fontSize: "12px", color: "#b09070", marginTop: "4px", fontFamily: "sans-serif" }}>
                    {form.duration} דקות • {form.format || "וידאו"}
                  </div>
                </div>
                <div style={{
                  background: "#f5efe5", borderRadius: "10px", padding: "10px 14px", textAlign: "center",
                }}>
                  <div style={{ fontSize: "10px", color: "#b09070", letterSpacing: "1px", fontFamily: "sans-serif" }}>תאמבנייל</div>
                  <div style={{ fontSize: "15px", fontWeight: 700, color: "#8a6030", marginTop: "4px" }}>
                    {result.thumbnail_text}
                  </div>
                </div>
              </div>
            </div>

            {/* Section tabs */}
            <div style={{ display: "flex", gap: "6px", marginBottom: "16px", overflowX: "auto", paddingBottom: "4px" }}>
              {SECTIONS.map(s => (
                <button key={s.id} onClick={() => setActiveSection(s.id)} style={{
                  background: activeSection === s.id ? "#8a6030" : "#fff",
                  color: activeSection === s.id ? "#fff" : "#9a8060",
                  border: `1px solid ${activeSection === s.id ? "#8a6030" : "#e8dcc8"}`,
                  borderRadius: "8px", padding: "8px 14px", fontSize: "12px", fontWeight: 600,
                  cursor: "pointer", whiteSpace: "nowrap", fontFamily: "sans-serif", transition: "all 0.2s",
                }}>
                  {s.label}
                </button>
              ))}
            </div>

            {/* Section content */}
            <div style={{
              background: "#fff", border: "1px solid #e8dcc8", borderRadius: "14px",
              padding: "24px", boxShadow: "0 4px 24px rgba(139,96,48,0.06)",
              marginBottom: "16px",
            }}>

              {activeSection === "titles" && (
                <div>
                  <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "16px", fontFamily: "sans-serif", letterSpacing: "0.5px" }}>
                    3 אפשרויות לכותרת
                  </div>
                  {result.title_options.map((t, i) => (
                    <div key={i} style={{
                      background: "#f8f4ee", borderRadius: "10px", padding: "14px 16px",
                      marginBottom: "10px", display: "flex", justifyContent: "space-between", alignItems: "center",
                    }}>
                      <div style={{ fontSize: "15px", color: "#2a1f0e", fontWeight: i === 0 ? 700 : 400 }}>
                        {i === 0 && <span style={{ color: "#8a6030", fontSize: "11px", fontFamily: "sans-serif", marginLeft: "8px" }}>מומלץ</span>}
                        {t}
                      </div>
                      <CopyBtn text={t} id={`title_${i}`} />
                    </div>
                  ))}
                </div>
              )}

              {activeSection === "precall" && (
                <div>
                  <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "12px", fontFamily: "sans-serif" }}>
                    סקריפט לשיחה המקדימה עם {form.name}
                  </div>
                  <div style={{ fontSize: "12px", color: "#9a8060", marginBottom: "14px", fontStyle: "italic", fontFamily: "sans-serif" }}>
                    זוהי שיחה פרטית בינך לבינה — הכנה וסנכרון לפני הראיון עצמו
                  </div>
                  <div style={{
                    background: "#f8f4ee", borderRadius: "10px", padding: "18px",
                    marginBottom: "20px", fontSize: "14px", color: "#2a1f0e", lineHeight: 2,
                    whiteSpace: "pre-wrap", direction: "rtl",
                  }}>
                    {result.pre_call_script}
                  </div>
                  <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: "10px" }}>
                    <div style={{ fontSize: "12px", fontWeight: 700, color: "#9a8060", fontFamily: "sans-serif", letterSpacing: "0.5px" }}>
                      בקשות ספציפיות ממנה
                    </div>
                    <CopyBtn text={result.pre_call_script} id="precall_script" />
                  </div>
                  {result.pre_call_requests.map((req, i) => (
                    <div key={i} style={{
                      display: "flex", gap: "12px", marginBottom: "10px", alignItems: "flex-start",
                      background: "#fff8f0", border: "1px solid #f0d8b0", borderRadius: "8px", padding: "10px 14px",
                    }}>
                      <div style={{
                        minWidth: "22px", height: "22px", borderRadius: "50%",
                        background: "#8a6030", color: "#fff", display: "flex",
                        alignItems: "center", justifyContent: "center", fontSize: "11px",
                        fontFamily: "sans-serif", marginTop: "1px",
                      }}>{i + 1}</div>
                      <div style={{ fontSize: "14px", color: "#2a1f0e", lineHeight: 1.7 }}>{req}</div>
                    </div>
                  ))}
                  <div style={{
                    background: "#f8f4ee", borderRadius: "10px", padding: "14px 16px",
                    marginTop: "16px", fontSize: "14px", color: "#4a3520", lineHeight: 1.9,
                    fontStyle: "italic", borderRight: "3px solid #8a6030",
                  }}>
                    <div style={{ fontSize: "11px", color: "#8a6030", fontWeight: 700, marginBottom: "6px", fontFamily: "sans-serif" }}>פתיחה לראיון עצמו</div>
                    {result.opening}
                  </div>
                </div>
              )}

              {activeSection === "outline" && (
                <div>
                  <div style={{ display: "flex", justifyContent: "space-between", marginBottom: "16px" }}>
                    <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", fontFamily: "sans-serif" }}>
                      מבנה הראיון — {form.duration} דקות
                    </div>
                    <CopyBtn text={result.outline.map(s => `${s.segment} (${s.duration})\n${s.questions.join("\n")}`).join("\n\n")} id="full_outline" />
                  </div>
                  {result.outline.map((seg, i) => (
                    <div key={i} style={{
                      border: "1px solid #e8dcc8", borderRadius: "10px",
                      marginBottom: "12px", overflow: "hidden",
                    }}>
                      <div style={{
                        background: "#f5efe5", padding: "10px 16px",
                        display: "flex", justifyContent: "space-between", alignItems: "center",
                      }}>
                        <div style={{ display: "flex", gap: "10px", alignItems: "center" }}>
                          <span style={{
                            background: "#8a6030", color: "#fff", borderRadius: "5px",
                            padding: "2px 8px", fontSize: "11px", fontFamily: "sans-serif",
                          }}>{seg.duration}</span>
                          <span style={{ fontWeight: 700, color: "#2a1f0e", fontSize: "14px" }}>{seg.segment}</span>
                        </div>
                        <span style={{ fontSize: "12px", color: "#9a8060", fontStyle: "italic" }}>{seg.goal}</span>
                      </div>
                      <div style={{ padding: "12px 16px" }}>
                        {seg.questions.map((q, j) => (
                          <div key={j} style={{
                            display: "flex", gap: "8px", marginBottom: "8px", alignItems: "flex-start",
                          }}>
                            <span style={{ color: "#b09070", fontSize: "13px", marginTop: "2px" }}>›</span>
                            <span style={{ fontSize: "14px", color: "#2a1f0e", lineHeight: 1.6 }}>{q}</span>
                          </div>
                        ))}
                      </div>
                    </div>
                  ))}
                </div>
              )}

              {activeSection === "angles" && (
                <div>
                  <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "12px", fontFamily: "sans-serif" }}>
                    איפה שלומי מוסיף את הקול שלו
                  </div>
                  {result.shlomi_angles.map((a, i) => (
                    <div key={i} style={{
                      background: "#f8f4ee", borderRadius: "10px", padding: "14px 16px",
                      marginBottom: "10px", borderRight: "3px solid #8a6030",
                      fontSize: "14px", color: "#2a1f0e", lineHeight: 1.7,
                    }}>
                      {a}
                    </div>
                  ))}
                  <div style={{
                    background: "#f0f8e8", border: "1px solid #c8dca8", borderRadius: "10px",
                    padding: "14px 16px", marginTop: "8px",
                  }}>
                    <div style={{ fontSize: "11px", color: "#5a7a3a", fontWeight: 700, marginBottom: "6px", fontFamily: "sans-serif" }}>
                      הערה לסיום
                    </div>
                    <div style={{ fontSize: "13px", color: "#3a5a2a", lineHeight: 1.7 }}>
                      {result.closing_note}
                    </div>
                  </div>
                </div>
              )}

              {activeSection === "caution" && (
                <div>
                  <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "12px", fontFamily: "sans-serif" }}>
                    מה לשים לב אליו בראיון הזה
                  </div>
                  {result.caution_points.map((c, i) => (
                    <div key={i} style={{
                      background: "#fff8f0", border: "1px solid #f0d8b0", borderRadius: "10px",
                      padding: "14px 16px", marginBottom: "10px",
                      display: "flex", gap: "12px", alignItems: "flex-start",
                    }}>
                      <span style={{ fontSize: "18px" }}>⚠️</span>
                      <span style={{ fontSize: "14px", color: "#2a1f0e", lineHeight: 1.7 }}>{c}</span>
                    </div>
                  ))}
                </div>
              )}

              {activeSection === "checklist" && (
                <div>
                  <div style={{ fontSize: "13px", fontWeight: 700, color: "#8a6030", marginBottom: "6px", fontFamily: "sans-serif" }}>
                    צ'ק ליסט — מה לבקש במהלך השיחה המקדימה או לאחר הראיון
                  </div>
                  <div style={{ fontSize: "12px", color: "#b09070", marginBottom: "16px", fontFamily: "sans-serif" }}>
                    סמן כל פריט כשהוא הושלם
                  </div>
                  {[
                    { id: "photo", category: "תמונה ותדמית", items: [
                      `בקש תמונה מקצועית של ${form.name} ברזולוציה גבוהה (לתאמבנייל)`,
                      "שאל אם יש לוגו שניתן להוסיף",
                    ]},
                    { id: "intro", category: "הצגה ואשרור", items: [
                      `אשר איך ${form.name} רוצה שיציגו אותו/ה — בדיוק`,
                    ]},
                    { id: "tech", category: "טכני (זום)", items: [
                      "ודא שיש מיקרופון איכותי / אוזניות",
                      "ודא תאורה טובה מלפנים (לא מאחור)",
                      "בקש רקע נקי או מקצועי",
                      "שלח לינק זום מראש וודא שהוא עובד",
                    ]},
                    { id: "content", category: "תוכן ואישורים", items: [
                      "הסבר על הקהל — מה הם מחפשים ומה יעזור להם",
                      "שאל האם יש נושאים שאין לגעת בהם",
                      "הסכם על משך הראיון — " + form.duration + " דקות",
                      "שאל האם רוצה לראות את השאלות מראש",
                      "קבל אישור לפרסום הוידאו בפייסבוק וביוטיוב",
                    ]},
                    { id: "post", category: "אחרי הראיון", items: [
                      `שלח ל${form.name} קישור לוידאו כשעולה`,
                      "בקש שיגיד על הוידאו ברשתות שלו/ה",
                      "שמור קשר לשיתופי פעולה עתידיים",
                    ]},
                  ].map(group => (
                    <div key={group.id} style={{ marginBottom: "20px" }}>
                      <div style={{
                        fontSize: "11px", fontWeight: 700, color: "#8a6030",
                        letterSpacing: "1px", marginBottom: "10px", fontFamily: "sans-serif",
                        textTransform: "uppercase",
                      }}>
                        {group.category}
                      </div>
                      {group.items.map((item, i) => {
                        const key = `${group.id}_${i}`;
                        const checked = checkedItems[key];
                        return (
                          <div key={key} onClick={() => setCheckedItems(prev => ({ ...prev, [key]: !prev[key] }))}
                            style={{
                              display: "flex", gap: "12px", alignItems: "flex-start",
                              padding: "10px 14px", borderRadius: "8px", marginBottom: "6px",
                              background: checked ? "#f0f8e8" : "#f8f4ee",
                              border: `1px solid ${checked ? "#c8dca8" : "#e8dcc8"}`,
                              cursor: "pointer", transition: "all 0.2s",
                            }}>
                            <div style={{
                              minWidth: "20px", height: "20px", borderRadius: "5px",
                              border: `2px solid ${checked ? "#5a7a3a" : "#c8a878"}`,
                              background: checked ? "#5a7a3a" : "transparent",
                              display: "flex", alignItems: "center", justifyContent: "center",
                              fontSize: "12px", color: "#fff", marginTop: "1px", flexShrink: 0,
                              transition: "all 0.2s",
                            }}>
                              {checked ? "✓" : ""}
                            </div>
                            <span style={{
                              fontSize: "13px", color: checked ? "#5a7a3a" : "#2a1f0e",
                              lineHeight: 1.6, textDecoration: checked ? "line-through" : "none",
                              fontFamily: "sans-serif", transition: "all 0.2s",
                            }}>
                              {item}
                            </span>
                          </div>
                        );
                      })}
                    </div>
                  ))}
                  <div style={{
                    textAlign: "center", marginTop: "8px",
                    fontSize: "12px", color: "#b09070", fontFamily: "sans-serif",
                  }}>
                    {Object.values(checkedItems).filter(Boolean).length} / {2 + 1 + 4 + 5 + 3 + customItems.length} הושלמו
                  </div>

                  {/* Custom items */}
                  {customItems.length > 0 && (
                    <div style={{ marginTop: "20px" }}>
                      <div style={{
                        fontSize: "11px", fontWeight: 700, color: "#8a6030",
                        letterSpacing: "1px", marginBottom: "10px", fontFamily: "sans-serif",
                        textTransform: "uppercase",
                      }}>משימות נוספות</div>
                      {customItems.map((item, i) => {
                        const key = `custom_${i}`;
                        const checked = checkedItems[key];
                        return (
                          <div key={key} style={{
                            display: "flex", gap: "10px", alignItems: "center",
                            padding: "10px 14px", borderRadius: "8px", marginBottom: "6px",
                            background: checked ? "#f0f8e8" : "#f8f4ee",
                            border: `1px solid ${checked ? "#c8dca8" : "#e8dcc8"}`,
                          }}>
                            <div onClick={() => setCheckedItems(prev => ({ ...prev, [key]: !prev[key] }))}
                              style={{
                                minWidth: "20px", height: "20px", borderRadius: "5px",
                                border: `2px solid ${checked ? "#5a7a3a" : "#c8a878"}`,
                                background: checked ? "#5a7a3a" : "transparent",
                                display: "flex", alignItems: "center", justifyContent: "center",
                                fontSize: "12px", color: "#fff", flexShrink: 0,
                                cursor: "pointer", transition: "all 0.2s",
                              }}>
                              {checked ? "✓" : ""}
                            </div>
                            <span onClick={() => setCheckedItems(prev => ({ ...prev, [key]: !prev[key] }))}
                              style={{
                                fontSize: "13px", color: checked ? "#5a7a3a" : "#2a1f0e",
                                lineHeight: 1.6, textDecoration: checked ? "line-through" : "none",
                                fontFamily: "sans-serif", cursor: "pointer", flex: 1,
                              }}>
                              {item}
                            </span>
                            <button onClick={() => setCustomItems(prev => prev.filter((_, idx) => idx !== i))}
                              style={{
                                background: "transparent", border: "none", color: "#c8a878",
                                cursor: "pointer", fontSize: "16px", lineHeight: 1, padding: "0 2px",
                              }}>×</button>
                          </div>
                        );
                      })}
                    </div>
                  )}

                  {/* Add new item */}
                  <div style={{
                    marginTop: "16px", display: "flex", gap: "8px", alignItems: "center",
                  }}>
                    <input
                      value={newItemText}
                      onChange={e => setNewItemText(e.target.value)}
                      onKeyDown={e => {
                        if (e.key === "Enter" && newItemText.trim()) {
                          setCustomItems(prev => [...prev, newItemText.trim()]);
                          setNewItemText("");
                        }
                      }}
                      placeholder="+ הוסף משימה..."
                      style={{
                        flex: 1, background: "#f8f4ee", border: "1.5px dashed #c8a878",
                        borderRadius: "8px", padding: "10px 14px", color: "#2a1f0e",
                        fontSize: "13px", outline: "none", fontFamily: "sans-serif", direction: "rtl",
                      }}
                    />
                    <button
                      onClick={() => {
                        if (newItemText.trim()) {
                          setCustomItems(prev => [...prev, newItemText.trim()]);
                          setNewItemText("");
                        }
                      }}
                      style={{
                        background: "#8a6030", color: "#fff", border: "none",
                        borderRadius: "8px", padding: "10px 16px", fontSize: "13px",
                        fontWeight: 700, cursor: "pointer", fontFamily: "sans-serif",
                        whiteSpace: "nowrap",
                      }}>
                      הוסף
                    </button>
                  </div>
                </div>
              )}
            </div>

            <div style={{ textAlign: "center", marginTop: "16px" }}>
              <button onClick={() => { setResult(null); setStep(0); setCheckedItems({}); setCustomItems([]); setNewItemText(""); setShowArchive(false); setForm({ name:"",title:"",expertise:"",bio:"",topic:"",angle:"",audience_specific:"סובלים מכאבי גב כרוניים",goal_primary:"",goal_secondary:"",duration:"45",format:"זום",notes:"" }); }} style={{
                background: "transparent", color: "#b09070", border: "none",
                fontSize: "13px", cursor: "pointer", fontFamily: "sans-serif",
              }}>
                &larr; ראיון חדש
              </button>
            </div>
          </div>
        )}
      </div>

      <style>{`
        @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
        input:focus, textarea:focus { border-color: #8a6030 !important; }
        input::placeholder, textarea::placeholder { color: #c8b898; }
        * { box-sizing: border-box; }
        ::-webkit-scrollbar { height: 4px; }
        ::-webkit-scrollbar-track { background: #f0e8d8; }
        ::-webkit-scrollbar-thumb { background: #c8a878; border-radius: 4px; }
      `}</style>
    </div>
  );
}
