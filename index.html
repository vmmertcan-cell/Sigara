<!DOCTYPE html>

<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="apple-mobile-web-app-title" content="Sigara Azalt" />
  <meta name="theme-color" content="#F2F2F7" />
  <title>Sigara Azalt</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/react/18.2.0/umd/react.production.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.2.0/umd/react-dom.production.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/7.23.2/babel.min.js"></script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
    body { background: #F2F2F7; overscroll-behavior: none; }
    input[type=number]::-webkit-inner-spin-button,
    input[type=number]::-webkit-outer-spin-button { -webkit-appearance: none; }
  </style>
</head>
<body>
  <div id="root"></div>
  <script type="text/babel">
    const { useState, useEffect } = React;

```
const TODAY = () => new Date().toISOString().split("T")[0];
const addDays = (d, n) => { const x = new Date(d); x.setDate(x.getDate() + n); return x.toISOString().split("T")[0]; };
const diffDays = (a, b) => Math.floor((new Date(b) - new Date(a)) / 86400000);

const INIT = {
  bugunIcilen: 0,
  toplamIcilen: 0,
  sonGun: TODAY(),
  baslangic: TODAY(),
  gecmis: {},
  plan: null,
  paketFiyati: 75,
  paketAdet: 20,
};

const STORAGE_KEY = "sigara_azalt_v1";

function load() {
  try { const s = localStorage.getItem(STORAGE_KEY); return s ? JSON.parse(s) : null; } catch { return null; }
}
function store(x) {
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(x)); } catch {}
}

function getPlanHedef(plan) {
  if (!plan) return null;
  const i = diffDays(plan.baslangic, TODAY());
  if (i < 0 || i >= plan.gunler.length) return null;
  return plan.gunler[i];
}

function buildPlan(baslangic, bitis, gun) {
  const gunler = [];
  for (let i = 0; i < gun; i++) {
    gunler.push(Math.round(baslangic - ((baslangic - bitis) / (gun - 1)) * i));
  }
  return { baslangic: TODAY(), gunler };
}

function App() {
  const [d, setD] = useState(INIT);
  const [tab, setTab] = useState("ana");
  const [pulse, setPulse] = useState(false);
  const [planDuzenle, setPlanDuzenle] = useState(false);
  const [pf, setPf] = useState({ bas: "", bit: "", gun: "30" });
  const [grafikMod, setGrafikMod] = useState(7);

  useEffect(() => {
    const s = load();
    if (!s) { setD({ ...INIT, sonGun: TODAY(), baslangic: TODAY() }); return; }
    if (s.sonGun !== TODAY()) {
      const g = { ...s.gecmis, [s.sonGun]: s.bugunIcilen };
      const nd = { ...s, bugunIcilen: 0, sonGun: TODAY(), gecmis: g };
      store(nd); setD(nd);
    } else setD(s);
  }, []);

  const save = (x) => { store(x); setD(x); };

  const ic = () => {
    setPulse(true); setTimeout(() => setPulse(false), 400);
    save({ ...d, bugunIcilen: d.bugunIcilen + 1, toplamIcilen: d.toplamIcilen + 1 });
  };
  const geri = () => {
    if (!d.bugunIcilen) return;
    save({ ...d, bugunIcilen: d.bugunIcilen - 1, toplamIcilen: Math.max(0, d.toplamIcilen - 1) });
  };

  const planHedef = getPlanHedef(d.plan);
  const hedef = planHedef !== null ? planHedef : 10;
  const oran = Math.min(d.bugunIcilen / Math.max(hedef, 1), 1);
  const asim = d.bugunIcilen > hedef;
  const accent = asim ? "#FF3B30" : d.bugunIcilen === 0 ? "#34C759" : d.bugunIcilen < hedef * 0.6 ? "#30D158" : "#FF9500";

  const grafikVerisi = (() => {
    const bugun = TODAY();
    return Array.from({ length: grafikMod }, (_, i) => {
      const t = addDays(bugun, -(grafikMod - 1 - i));
      const val = t === bugun ? d.bugunIcilen : (d.gecmis[t] ?? null);
      const planVal = d.plan ? (() => {
        const gi = diffDays(d.plan.baslangic, t);
        return gi >= 0 && gi < d.plan.gunler.length ? d.plan.gunler[gi] : null;
      })() : null;
      return { t, val, planVal, label: new Date(t).toLocaleDateString("tr-TR", { day: "numeric", month: "short" }) };
    });
  })();

  const maxBar = Math.max(...grafikVerisi.map(g => Math.max(g.val ?? 0, g.planVal ?? 0, 1)), hedef);
  const planGun = d.plan ? Math.min(Math.max(diffDays(d.plan.baslangic, TODAY()), 0), d.plan.gunler.length - 1) : 0;
  const planYuzde = d.plan ? Math.round((planGun / (d.plan.gunler.length - 1)) * 100) : 0;
  const toplamGun = Math.max(1, diffDays(d.baslangic, TODAY()) + 1);
  const ort = (d.toplamIcilen / toplamGun).toFixed(1);
  const harcanan = ((d.toplamIcilen * d.paketFiyati) / d.paketAdet).toFixed(0);

  const S = {
    app: { minHeight: "100vh", background: "#F2F2F7", fontFamily: "-apple-system,'SF Pro Display','Helvetica Neue',sans-serif", display: "flex", flexDirection: "column", alignItems: "center", color: "#1C1C1E" },
    header: { width: "100%", maxWidth: 430, padding: "56px 24px 8px", display: "flex", justifyContent: "space-between", alignItems: "flex-end" },
    tabBar: { display: "flex", width: "100%", maxWidth: 430, padding: "0 16px", marginTop: 8 },
    tab: (a) => ({ flex: 1, padding: "10px 0", background: "none", border: "none", fontSize: 13, fontWeight: a ? 600 : 400, color: a ? "#007AFF" : "#8E8E93", cursor: "pointer", borderBottom: a ? "2px solid #007AFF" : "2px solid transparent", fontFamily: "inherit", transition: "all 0.15s" }),
    body: { width: "100%", maxWidth: 430, padding: "20px 16px 80px" },
    card: { background: "#fff", borderRadius: 20, padding: "20px", marginBottom: 12, boxShadow: "0 1px 3px rgba(0,0,0,0.06)" },
    row: { display: "flex", justifyContent: "space-between", alignItems: "center" },
    btn: (p) => ({ flex: p ? 2 : 1, padding: "16px 0", borderRadius: 14, border: "none", background: p ? accent : "#F2F2F7", color: p ? "#fff" : "#1C1C1E", fontSize: p ? 17 : 15, fontWeight: 600, cursor: "pointer", fontFamily: "inherit", transition: "all 0.2s" }),
    input: { width: "100%", background: "#F2F2F7", border: "none", borderRadius: 12, padding: "14px 16px", fontSize: 16, fontFamily: "inherit", outline: "none", color: "#1C1C1E", boxSizing: "border-box" },
    pill: (a) => ({ padding: "6px 16px", borderRadius: 20, border: "none", background: a ? "#007AFF" : "#E5E5EA", color: a ? "#fff" : "#8E8E93", fontSize: 13, fontWeight: 500, cursor: "pointer", fontFamily: "inherit" }),
  };

  return (
    <div style={S.app}>
      {/* Header */}
      <div style={S.header}>
        <div>
          <div style={{ fontSize: 34, fontWeight: 700, letterSpacing: -0.5 }}>Sigara</div>
          <div style={{ fontSize: 15, color: "#8E8E93", marginTop: 2 }}>
            {new Date().toLocaleDateString("tr-TR", { weekday: "long", day: "numeric", month: "long" })}
          </div>
        </div>
        <div style={{ textAlign: "right" }}>
          <div style={{ fontSize: 28, fontWeight: 700, color: accent, transition: "color 0.3s" }}>{d.bugunIcilen}</div>
          <div style={{ fontSize: 12, color: "#8E8E93" }}>/ {hedef} hedef</div>
        </div>
      </div>

      {/* Tabs */}
      <div style={S.tabBar}>
        {[["ana","Bugün"],["grafik","Grafik"],["plan","Plan"]].map(([id, lbl]) => (
          <button key={id} style={S.tab(tab===id)} onClick={() => setTab(id)}>{lbl}</button>
        ))}
      </div>

      <div style={S.body}>

        {/* BUGÜN */}
        {tab === "ana" && <>
          <div style={{ ...S.card, textAlign: "center", padding: "32px 20px 24px" }}>
            <div style={{ fontSize: 13, fontWeight: 600, color: "#8E8E93", textTransform: "uppercase", letterSpacing: 0.8, marginBottom: 16 }}>Bugün içilen</div>

            {/* Halka */}
            <div style={{ position: "relative", width: 160, height: 160, margin: "0 auto 16px" }}>
              <svg width="160" height="160" style={{ transform: "rotate(-90deg)" }}>
                <circle cx="80" cy="80" r="68" fill="none" stroke="#F2F2F7" strokeWidth="10" />
                <circle cx="80" cy="80" r="68" fill="none" stroke={accent} strokeWidth="10"
                  strokeDasharray={`${2 * Math.PI * 68}`}
                  strokeDashoffset={`${2 * Math.PI * 68 * (1 - oran)}`}
                  strokeLinecap="round"
                  style={{ transition: "stroke-dashoffset 0.5s ease, stroke 0.3s" }}
                />
              </svg>
              <div style={{ position: "absolute", inset: 0, display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "center" }}>
                <div style={{ fontSize: 52, fontWeight: 700, color: accent, lineHeight: 1, transform: pulse ? "scale(1.2)" : "scale(1)", transition: "transform 0.3s cubic-bezier(0.34,1.56,0.64,1), color 0.3s" }}>
                  {d.bugunIcilen}
                </div>
                <div style={{ fontSize: 13, color: "#8E8E93", marginTop: 2 }}>sigara</div>
              </div>
            </div>

            {/* Delta */}
            {(() => {
              const delta = d.bugunIcilen - hedef;
              const sifir = delta === 0;
              const poz = delta > 0;
              return (
                <div style={{ display: "inline-flex", alignItems: "center", gap: 8, background: sifir ? "#E5E5EA" : poz ? "#FFE5E5" : "#E8F8EF", borderRadius: 20, padding: "8px 20px", marginBottom: 18, transition: "all 0.3s" }}>
                  <span style={{ fontSize: 22, fontWeight: 700, color: sifir ? "#8E8E93" : poz ? "#FF3B30" : "#34C759", transition: "color 0.3s" }}>
                    {poz ? "+" : ""}{delta}
                  </span>
                  <span style={{ fontSize: 13, color: sifir ? "#8E8E93" : poz ? "#FF3B30" : "#34C759", fontWeight: 500 }}>
                    {sifir ? "Hedefte" : poz ? "hedef aşıldı" : "hedefin altında"}
                  </span>
                </div>
              );
            })()}

            <div style={{ fontSize: 15, color: "#3C3C43", marginBottom: 24, lineHeight: 1.5 }}>
              {d.bugunIcilen === 0 && "Henüz içmedin. Harika! 🎉"}
              {d.bugunIcilen > 0 && d.bugunIcilen < hedef && `${hedef - d.bugunIcilen} sigara kaldı.`}
              {d.bugunIcilen === hedef && "Hedefe ulaştın. Dur! 🛑"}
              {d.bugunIcilen > hedef && `Hedefi ${d.bugunIcilen - hedef} aştın.`}
            </div>

            <div style={{ display: "flex", gap: 10 }}>
              <button onClick={geri} disabled={!d.bugunIcilen} style={{ ...S.btn(false), opacity: d.bugunIcilen ? 1 : 0.35 }}>Geri Al</button>
              <button onClick={ic} style={S.btn(true)}>İçtim 🚬</button>
            </div>
          </div>

          {/* İstatistik */}
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 10, marginBottom: 12 }}>
            {[
              { val: d.toplamIcilen, lbl: "Toplam" },
              { val: ort, lbl: "Günlük ort." },
              { val: `₺${harcanan}`, lbl: "Harcandı" },
            ].map(({ val, lbl }) => (
              <div key={lbl} style={{ ...S.card, textAlign: "center", padding: "16px 8px", marginBottom: 0 }}>
                <div style={{ fontSize: 20, fontWeight: 700 }}>{val}</div>
                <div style={{ fontSize: 11, color: "#8E8E93", marginTop: 3 }}>{lbl}</div>
              </div>
            ))}
          </div>

          {d.plan && (
            <div style={{ ...S.card, background: "#EBF5FF", boxShadow: "none" }}>
              <div style={S.row}>
                <div>
                  <div style={{ fontSize: 13, fontWeight: 600, color: "#007AFF" }}>Aktif Plan</div>
                  <div style={{ fontSize: 12, color: "#636366", marginTop: 2 }}>Bugünün hedefi: <strong>{hedef}</strong></div>
                </div>
                <div style={{ fontSize: 13, fontWeight: 700, color: "#007AFF" }}>%{planYuzde}</div>
              </div>
              <div style={{ background: "#C7E2FF", borderRadius: 6, height: 4, marginTop: 10, overflow: "hidden" }}>
                <div style={{ width: `${planYuzde}%`, height: "100%", background: "#007AFF", borderRadius: 6, transition: "width 0.5s" }} />
              </div>
            </div>
          )}
        </>}

        {/* GRAFİK */}
        {tab === "grafik" && <>
          <div style={S.card}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
              <div style={{ fontSize: 17, fontWeight: 600 }}>Günlük Sigara</div>
              <div style={{ display: "flex", gap: 6 }}>
                {[7, 14, 30].map(n => (
                  <button key={n} onClick={() => setGrafikMod(n)} style={S.pill(grafikMod === n)}>{n}g</button>
                ))}
              </div>
            </div>
            <div style={{ display: "flex", alignItems: "flex-end", gap: grafikMod > 14 ? 2 : 6, height: 140, marginBottom: 8 }}>
              {grafikVerisi.map(({ t, val, planVal }) => {
                const h = val !== null ? Math.max((val / maxBar) * 130, 3) : 0;
                const ph = planVal !== null ? (planVal / maxBar) * 130 : 0;
                const over = val !== null && val > hedef;
                return (
                  <div key={t} style={{ flex: 1, display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "flex-end", height: "100%", position: "relative" }}>
                    {planVal !== null && <div style={{ position: "absolute", bottom: ph, width: "100%", borderTop: "1.5px dashed #007AFF44", zIndex: 1 }} />}
                    <div style={{ width: "100%", height: h, borderRadius: "5px 5px 0 0", background: val === null ? "#F2F2F7" : over ? "#FF3B30" : "#007AFF", opacity: val === null ? 0.4 : 1, transition: "height 0.4s ease" }} />
                  </div>
                );
              })}
            </div>
            <div style={{ display: "flex", justifyContent: "space-between" }}>
              <span style={{ fontSize: 10, color: "#8E8E93" }}>{grafikVerisi[0]?.label}</span>
              <span style={{ fontSize: 10, color: "#8E8E93" }}>{grafikVerisi[grafikVerisi.length-1]?.label}</span>
            </div>
            <div style={{ display: "flex", gap: 16, marginTop: 14, paddingTop: 12, borderTop: "1px solid #F2F2F7" }}>
              <div style={{ display: "flex", alignItems: "center", gap: 5 }}>
                <div style={{ width: 10, height: 10, borderRadius: 2, background: "#007AFF" }} />
                <span style={{ fontSize: 12, color: "#636366" }}>İçilen</span>
              </div>
              <div style={{ display: "flex", alignItems: "center", gap: 5 }}>
                <div style={{ width: 10, height: 10, borderRadius: 2, background: "#FF3B30" }} />
                <span style={{ fontSize: 12, color: "#636366" }}>Aşıldı</span>
              </div>
            </div>
          </div>

          <div style={S.card}>
            <div style={{ fontSize: 17, fontWeight: 600, marginBottom: 16 }}>Bu hafta</div>
            {(() => {
              const hv = grafikVerisi.slice(-7);
              const toplam = hv.reduce((s, g) => s + (g.val ?? 0), 0);
              const filtre = hv.filter(g => g.val !== null);
              const enAz = filtre.length ? Math.min(...filtre.map(g => g.val)) : "-";
              const enCok = Math.max(...hv.map(g => g.val ?? 0));
              return (
                <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12 }}>
                  {[{ val: toplam, lbl: "Toplam" }, { val: enAz, lbl: "En az" }, { val: enCok, lbl: "En çok" }].map(({ val, lbl }) => (
                    <div key={lbl} style={{ textAlign: "center" }}>
                      <div style={{ fontSize: 24, fontWeight: 700 }}>{val}</div>
                      <div style={{ fontSize: 12, color: "#8E8E93", marginTop: 2 }}>{lbl}</div>
                    </div>
                  ))}
                </div>
              );
            })()}
          </div>
        </>}

        {/* PLAN */}
        {tab === "plan" && <>
          {!d.plan ? (
            <div style={S.card}>
              <div style={{ textAlign: "center", padding: "16px 0 8px" }}>
                <div style={{ fontSize: 48, marginBottom: 12 }}>📉</div>
                <div style={{ fontSize: 20, fontWeight: 700, marginBottom: 8 }}>Azaltma Planı</div>
                <div style={{ fontSize: 15, color: "#636366", lineHeight: 1.6, marginBottom: 24 }}>
                  Günlük hedefler otomatik ayarlanır.
                </div>
                {[
                  { key: "bas", label: "Şu an günde kaç içiyorsun?", ph: "örn. 20" },
                  { key: "bit", label: "Hedefin kaç olsun?", ph: "örn. 3" },
                ].map(({ key, label, ph }) => (
                  <div key={key} style={{ textAlign: "left", marginBottom: 14 }}>
                    <div style={{ fontSize: 13, color: "#8E8E93", marginBottom: 6 }}>{label}</div>
                    <input style={S.input} type="number" placeholder={ph} value={pf[key]} onChange={e => setPf({...pf, [key]: e.target.value})} />
                  </div>
                ))}
                <div style={{ textAlign: "left", marginBottom: 24 }}>
                  <div style={{ fontSize: 13, color: "#8E8E93", marginBottom: 8 }}>Kaç günde ulaşmak istiyorsun?</div>
                  <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>
                    {[14, 21, 30, 60].map(n => (
                      <button key={n} onClick={() => setPf({...pf, gun: String(n)})} style={S.pill(pf.gun === String(n))}>{n} gün</button>
                    ))}
                  </div>
                </div>
                <button onClick={() => {
                  const b = parseInt(pf.bas), bi = parseInt(pf.bit), g = parseInt(pf.gun);
                  if (!isNaN(b) && !isNaN(bi) && !isNaN(g) && b > bi && g > 1) save({ ...d, plan: buildPlan(b, bi, g) });
                }} style={{ ...S.btn(true), display: "block", width: "100%", padding: "16px" }}>
                  Planı Başlat
                </button>
              </div>
            </div>
          ) : (
            <>
              <div style={{ ...S.card, background: "#EBF5FF", boxShadow: "none" }}>
                <div style={{ ...S.row, marginBottom: 12 }}>
                  <div style={{ fontSize: 13, fontWeight: 600, color: "#007AFF" }}>Aktif Plan</div>
                  <button onClick={() => { setPlanDuzenle(!planDuzenle); setPf({ bas: String(d.plan.gunler[planGun] ?? ""), bit: String(d.plan.gunler[d.plan.gunler.length - 1] ?? ""), gun: String(d.plan.gunler.length - planGun) }); }}
                    style={{ background: planDuzenle ? "#007AFF" : "#C7E2FF", border: "none", borderRadius: 10, padding: "5px 12px", fontSize: 12, fontWeight: 600, color: planDuzenle ? "#fff" : "#007AFF", cursor: "pointer", fontFamily: "inherit" }}>
                    {planDuzenle ? "Vazgeç" : "Güncelle"}
                  </button>
                </div>

                {planDuzenle ? (
                  <div>
                    <div style={{ fontSize: 12, color: "#636366", marginBottom: 12 }}>Bugünden itibaren yeniden ayarla</div>
                    {[{ key: "bas", label: "Bugünün hedefi" }, { key: "bit", label: "Bitiş hedefi" }].map(({ key, label }) => (
                      <div key={key} style={{ marginBottom: 10 }}>
                        <div style={{ fontSize: 12, color: "#8E8E93", marginBottom: 5 }}>{label}</div>
                        <input type="number" value={pf[key]} onChange={e => setPf({ ...pf, [key]: e.target.value })}
                          style={{ ...S.input, background: "#fff", padding: "10px 14px", fontSize: 15 }} />
                      </div>
                    ))}
                    <div style={{ marginBottom: 14 }}>
                      <div style={{ fontSize: 12, color: "#8E8E93", marginBottom: 8 }}>Kalan gün</div>
                      <div style={{ display: "flex", gap: 6, flexWrap: "wrap" }}>
                        {[7, 14, 21, 30].map(n => (
                          <button key={n} onClick={() => setPf({ ...pf, gun: String(n) })} style={S.pill(pf.gun === String(n))}>{n}g</button>
                        ))}
                      </div>
                    </div>
                    <button onClick={() => {
                      const b = parseInt(pf.bas), bi = parseInt(pf.bit), g = parseInt(pf.gun);
                      if (!isNaN(b) && !isNaN(bi) && !isNaN(g) && b >= bi && g > 0) {
                        save({ ...d, plan: buildPlan(b, bi, g) });
                        setPlanDuzenle(false);
                      }
                    }} style={{ width: "100%", padding: "12px", borderRadius: 12, border: "none", background: "#007AFF", color: "#fff", fontSize: 15, fontWeight: 600, cursor: "pointer", fontFamily: "inherit" }}>
                      Güncelle
                    </button>
                  </div>
                ) : (
                  <>
                    <div style={S.row}>
                      <div style={{ fontSize: 28, fontWeight: 700 }}>{planGun + 1}. gün</div>
                      <div style={{ fontSize: 13, color: "#636366" }}>{d.plan.gunler.length} günden</div>
                    </div>
                    <div style={{ background: "#C7E2FF", borderRadius: 6, height: 6, margin: "12px 0", overflow: "hidden" }}>
                      <div style={{ width: `${planYuzde}%`, height: "100%", background: "#007AFF", borderRadius: 6, transition: "width 0.5s" }} />
                    </div>
                    <div style={S.row}>
                      <div style={{ fontSize: 13, color: "#636366" }}>Bugünün hedefi: <strong style={{ color: "#1C1C1E" }}>{hedef}</strong></div>
                      <div style={{ fontSize: 13, color: "#636366" }}>%{planYuzde}</div>
                    </div>
                  </>
                )}
              </div>

              <div style={S.card}>
                <div style={{ fontSize: 17, fontWeight: 600, marginBottom: 14 }}>Günlük Hedefler</div>
                <div style={{ display: "flex", flexDirection: "column", gap: 2 }}>
                  {d.plan.gunler.slice(Math.max(0, planGun - 2), planGun + 12).map((hedefVal, idx) => {
                    const gIdx = Math.max(0, planGun - 2) + idx;
                    const tarih = addDays(d.plan.baslangic, gIdx);
                    const gecti = tarih < TODAY();
                    const bugunMu = tarih === TODAY();
                    const gercek = gecti ? (d.gecmis[tarih] ?? null) : bugunMu ? d.bugunIcilen : null;
                    const basarili = gercek !== null && gercek <= hedefVal;
                    return (
                      <div key={gIdx} style={{ display: "flex", alignItems: "center", gap: 12, padding: "10px 12px", borderRadius: 12, background: bugunMu ? "#EBF5FF" : "transparent", opacity: gIdx > planGun + 7 ? 0.4 : 1 }}>
                        <div style={{ width: 32, height: 32, borderRadius: "50%", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 13, fontWeight: 600, flexShrink: 0, background: bugunMu ? "#007AFF" : gecti ? (basarili ? "#34C75922" : "#FF3B3022") : "#F2F2F7", color: bugunMu ? "#fff" : gecti ? (basarili ? "#34C759" : "#FF3B30") : "#8E8E93" }}>
                          {gecti ? (basarili ? "✓" : "✗") : gIdx + 1}
                        </div>
                        <div style={{ flex: 1 }}>
                          <div style={{ fontSize: 14, fontWeight: bugunMu ? 600 : 400, color: bugunMu ? "#007AFF" : "#1C1C1E" }}>
                            {new Date(tarih).toLocaleDateString("tr-TR", { weekday: "short", day: "numeric", month: "short" })}
                            {bugunMu && " · Bugün"}
                          </div>
                        </div>
                        <div style={{ textAlign: "right" }}>
                          <div style={{ fontSize: 17, fontWeight: 700, color: bugunMu ? "#007AFF" : "#1C1C1E" }}>{hedefVal}</div>
                          {gercek !== null && <div style={{ fontSize: 11, color: basarili ? "#34C759" : "#FF3B30" }}>{gercek}</div>}
                        </div>
                      </div>
                    );
                  })}
                </div>
              </div>

              <button onClick={() => save({ ...d, plan: null })} style={{ width: "100%", padding: "14px", borderRadius: 14, border: "none", background: "#FFE5E5", color: "#FF3B30", fontSize: 15, fontWeight: 600, cursor: "pointer", fontFamily: "inherit", marginBottom: 12 }}>
                Planı İptal Et
              </button>
            </>
          )}

          <div style={S.card}>
            <div style={{ fontSize: 17, fontWeight: 600, marginBottom: 14 }}>Ayarlar</div>
            <div style={{ ...S.row, marginBottom: 14 }}>
              <div style={{ fontSize: 15 }}>Paket fiyatı (₺)</div>
              <input type="number" defaultValue={d.paketFiyati}
                onBlur={e => { const v = parseFloat(e.target.value); if (!isNaN(v) && v > 0) save({ ...d, paketFiyati: v }); }}
                style={{ width: 80, background: "#F2F2F7", border: "none", borderRadius: 10, padding: "8px 12px", fontSize: 15, fontFamily: "inherit", outline: "none", textAlign: "right", color: "#007AFF", fontWeight: 600 }}
              />
            </div>
            <button onClick={() => { const t = TODAY(); save({ ...INIT, sonGun: t, baslangic: t }); }}
              style={{ width: "100%", padding: "12px", borderRadius: 12, border: "none", background: "#FFE5E5", color: "#FF3B30", fontSize: 14, fontWeight: 500, cursor: "pointer", fontFamily: "inherit" }}>
              Tüm Verileri Sıfırla
            </button>
          </div>
        </>}
      </div>
    </div>
  );
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

  </script>
</body>
</html>
