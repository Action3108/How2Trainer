import { useState, useMemo } from "react";

/* =========================================================================
   Trainingsplaner SV Schöning — MVP (Single-File-Version für Vorschau)
   Lokale Projektstruktur: siehe Kommentar-Blöcke — jeder Abschnitt
   entspricht einer Datei aus src/ (types, data, utils, components).
   ========================================================================= */

/* ====================== src/types/training.ts ============================
   AgeGroup: 'Minis' | 'F-Jugend' | ... | 'A-Jugend'
   Focus: 'pass' | 'eins' | 'fitness'
   Block: 'warmIndividual' | 'warmGeneral' | 'warmBall' | 'game1' | 'drill' | 'game2' | 'final'
   Exercise: { id, title, ageGroups, focusAreas, blockType, duration,
               minPlayers, maxPlayers, material, objective, setup(n),
               flow, coachingPoints, coachCommands, easierVariation,
               harderVariation, svgDiagramType }
   ========================================================================= */

const AGE_GROUPS = ["Minis", "F-Jugend", "E-Jugend", "D-Jugend", "C-Jugend", "B-Jugend", "A-Jugend"];
const YOUNG = ["Minis", "F-Jugend", "E-Jugend"];
const MID = ["D-Jugend"];
const OLD = ["C-Jugend", "B-Jugend", "A-Jugend"];
const MID_OLD = [...MID, ...OLD];
const ALL_AGES = [...YOUNG, ...MID_OLD];

const FOCUS_OPTIONS = [
  { value: "pass", label: "Passspiel" },
  { value: "eins", label: "1 gegen 1 Verhalten" },
  { value: "fitness", label: "Fitness" },
];
const ALL_FOCUS = ["pass", "eins", "fitness"];

const BLOCKS = [
  { type: "warmIndividual", label: "Block 1 · Individuelles Aufwärmen", duration: 10 },
  { type: "warmGeneral", label: "Block 2 · Allgemeines Aufwärmen", duration: 10 },
  { type: "warmBall", label: "Block 3 · Aufwärmen mit Ball", duration: 10 },
  { type: "game1", label: "Block 4 · Erste Spielform", duration: 15 },
  { type: "drill", label: "Block 5 · Übungsblock", duration: 20 },
  { type: "game2", label: "Block 6 · Zweite Spielform", duration: 15 },
  { type: "final", label: "Block 7 · Abschlussspiel", duration: 10 },
];

/* Skaliert die 90-Minuten-Basisstruktur auf eine beliebige Gesamtdauer
   (in 5-Minuten-Schritten). Jeder Block bleibt ein Vielfaches von 5 Min,
   die Summe entspricht exakt der gewählten Gesamtdauer. */
function scaleBlocks(totalMinutes) {
  const factor = totalMinutes / 90;
  const scaled = BLOCKS.map((b) => ({
    ...b,
    duration: Math.max(5, Math.round((b.duration * factor) / 5) * 5),
  }));
  let diff = totalMinutes - scaled.reduce((s, b) => s + b.duration, 0);
  // Differenz in 5er-Schritten auf die Spiel-/Übungsblöcke verteilen
  const adjustOrder = [4, 3, 5, 6, 2, 1, 0];
  let i = 0;
  while (diff !== 0 && i < 50) {
    const idx = adjustOrder[i % adjustOrder.length];
    const step = diff > 0 ? 5 : -5;
    if (scaled[idx].duration + step >= 5) {
      scaled[idx].duration += step;
      diff -= step;
    }
    i++;
  }
  return scaled;
}

/* ---- Hilfsfunktionen für spieleranzahl-abhängige Organisation ---- */
const groupsOf = (n, size) => {
  const g = Math.max(1, Math.round(n / size));
  const per = Math.floor(n / g);
  const rest = n - per * g;
  return rest === 0
    ? `${g} Gruppe${g > 1 ? "n" : ""} à ${per} Spieler`
    : `${g} Gruppen (${g - rest}× ${per}, ${rest}× ${per + 1} Spieler)`;
};
const teamsLabel = (n) => {
  const half = Math.floor(n / 2);
  return n % 2 === 0 ? `${half} gegen ${half}` : `${half} gegen ${half} + 1 neutraler Spieler (Joker)`;
};

/* ====================== src/data/exercises.ts ============================ */
const EXERCISES = [
  /* ---------- Block 1: Individuelles Aufwärmen ---------- */
  {
    id: "wi-young-1",
    title: "Freies Ankommen & Bewegungslandschaft",
    ageGroups: YOUNG, focusAreas: ALL_FOCUS, blockType: "warmIndividual",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "8–12 Hütchen, 2–3 Reifen oder Markierungen",
    objective: "Spielerisch ankommen, Körper aufwecken, Freude an Bewegung.",
    setup: (n) => `Feld ca. 20×20 m, frei verteilt. ${n} Kinder bewegen sich gleichzeitig, keine Wartezeiten.`,
    flow: "Kinder bewegen sich frei im Feld. Trainer ruft Tierbewegungen: Bärengang, Hasenhüpfen, Storchengang, Krebsgang. Zwischendurch kurze Sprints zu einer Farbe (Hütchen).",
    coachingPoints: ["Alle in Bewegung halten", "Aufgaben kurz und bildhaft erklären", "Loben, nicht korrigieren"],
    coachCommands: ["Zeigt mir den Bären!", "Schnell zum roten Hütchen!", "Wer schafft drei Hüpfer am Stück?"],
    easierVariation: "Nur 2–3 einfache Bewegungen, längere Phasen pro Aufgabe.",
    harderVariation: "Bewegungen kombinieren (z. B. Hüpfen + Drehung), Reaktionssignale einbauen.",
    svgDiagramType: "freeArea",
  },
  {
    id: "wi-old-1",
    title: "Individuelles Einlaufen & Mobilisation",
    ageGroups: MID_OLD, focusAreas: ALL_FOCUS, blockType: "warmIndividual",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "4 Hütchen für ein Feld 25×25 m",
    objective: "Herz-Kreislauf aktivieren, Muskulatur und Gelenke auf Belastung vorbereiten.",
    setup: (n) => `Feld 25×25 m. ${n} Spieler verteilen sich, jeder arbeitet im eigenen Tempo.`,
    flow: "5 Min lockeres Einlaufen im Feld mit Richtungswechseln. Danach Mobilisation: Armkreisen, Hüftöffner/-schließer, Ausfallschritte, Beinpendel, kurze Steigerungsläufe zum Abschluss.",
    coachingPoints: ["Saubere Ausführung vor Tempo", "Eigenverantwortung einfordern", "Letzte Steigerungen mit Tempo"],
    coachCommands: ["Locker bleiben", "Große Bewegungen", "Letzte zwei Läufe mit Zug"],
    easierVariation: "Trainer gibt jede Übung vor und macht sie mit.",
    harderVariation: "Spieler führen Aufwärmen selbst (Routine), Trainer beobachtet nur.",
    svgDiagramType: "freeArea",
  },

  /* ---------- Block 2: Allgemeines Aufwärmen ---------- */
  {
    id: "wg-young-1",
    title: "Feuer, Wasser, Sturm",
    ageGroups: YOUNG, focusAreas: ALL_FOCUS, blockType: "warmGeneral",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "Hütchen für Feld 20×20 m, 3–4 Reifen",
    objective: "Reaktion, Orientierung und schnelles Umschalten zwischen Aufgaben.",
    setup: (n) => `Feld 20×20 m, Reifen als „Inseln“ am Rand. ${n} Kinder laufen frei.`,
    flow: "Kinder laufen frei. Auf Kommando: „Feuer“ = in eine Ecke sprinten, „Wasser“ = auf eine Insel (Reifen), „Sturm“ = flach auf den Boden. Kommandos zunehmend schneller wechseln.",
    coachingPoints: ["Klare, laute Kommandos", "Tempo allmählich steigern", "Zusammenstöße vermeiden – Kopf hoch"],
    coachCommands: ["Kopf hoch!", "Schneller reagieren!", "Augen auf, Platz suchen!"],
    easierVariation: "Nur zwei Kommandos, langsames Tempo.",
    harderVariation: "Vier Kommandos, zusätzlich mit Ball am Fuß.",
    svgDiagramType: "freeArea",
  },
  {
    id: "wg-old-1",
    title: "Lauf-ABC mit Koordinationsaufgaben",
    ageGroups: MID_OLD, focusAreas: ALL_FOCUS, blockType: "warmGeneral",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "10–12 Hütchen, optional Koordinationsleiter",
    objective: "Lauftechnik, Koordination und Aktivierung vor intensiven Inhalten.",
    setup: (n) => `2 parallele Bahnen à 15 m. ${groupsOf(n, Math.ceil(n / 2))} – Start versetzt, zurück außen herum traben.`,
    flow: "Bahnen mit wechselnden Aufgaben: Skippings, Anfersen, Hopserlauf, Seitstellschritte, Kreuzschritte. Abschluss: 2–3 Steigerungsläufe mit Sprint auf den letzten 5 m.",
    coachingPoints: ["Aufrechte Körperhaltung", "Aktiver Fußaufsatz", "Armarbeit mitnehmen"],
    coachCommands: ["Knie hoch!", "Frequenz!", "Letzte Meter Vollgas!"],
    easierVariation: "Weniger Aufgaben, mehr Wiederholungen derselben Form.",
    harderVariation: "Aufgaben kombinieren, Reaktionssprints auf Signal (akustisch/visuell).",
    svgDiagramType: "lanes",
  },

  /* ---------- Block 3: Individuelles Aufwärmen mit Ball ---------- */
  {
    id: "wb-young-1",
    title: "Dribbel-Zoo",
    ageGroups: YOUNG, focusAreas: ALL_FOCUS, blockType: "warmBall",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Kind, Hütchen für Feld 20×20 m",
    objective: "Viele Ballkontakte, Ballgefühl, erste enge Ballführung.",
    setup: (n) => `Feld 20×20 m, jedes der ${n} Kinder mit eigenem Ball.`,
    flow: "Alle dribbeln frei. Aufgaben: „Schnecke“ (ganz langsam, viele Kontakte), „Pferd“ (Tempo), „Stopp-Tier“ (Ball mit Sohle stoppen), „Elefant“ (nur schwacher Fuß).",
    coachingPoints: ["Ball nah am Fuß", "Beide Füße einsetzen", "Blick immer wieder vom Ball lösen"],
    coachCommands: ["Kopf hoch!", "Ganz viele Kontakte!", "Auch der andere Fuß!"],
    easierVariation: "Ball darf mit der Hand gerollt werden, größeres Feld.",
    harderVariation: "Zusatzsignal: Auf Pfiff Ball stoppen und freien Ball eines anderen suchen.",
    svgDiagramType: "dribbleField",
  },
  {
    id: "wb-pass-1",
    title: "Passpendel in Dreiergruppen",
    ageGroups: MID_OLD, focusAreas: ["pass"], blockType: "warmBall",
    duration: 10, minPlayers: 6, maxPlayers: 24,
    material: "1 Ball pro Gruppe, 2 Hütchen pro Gruppe (Abstand 10–12 m)",
    objective: "Passqualität und erster Kontakt unter leichter Bewegung.",
    setup: (n) => `${groupsOf(n, 3)}. Pro Gruppe zwei Hütchen, Abstand 10–12 m. Passen und dem Pass nachlaufen.`,
    flow: "A passt zu B und läuft dem Ball nach. B nimmt offen mit, passt zu C, läuft nach. Nach 3 Min: Mitnahme nur mit erstem Kontakt in Laufrichtung, dann Doppelpass vor dem langen Pass.",
    coachingPoints: ["Offene Stellung vor Ballannahme", "Erster Kontakt in Spielrichtung", "Scharfes, flaches Zuspiel"],
    coachCommands: ["Erster Kontakt in Spielrichtung!", "Offen stehen!", "Tempo nach der Aktion!"],
    easierVariation: "Geringerer Abstand, Mitnahme mit beliebig vielen Kontakten.",
    harderVariation: "Nur 2 Kontakte, schwacher Fuß, oder direkter Doppelpass als Pflicht.",
    svgDiagramType: "passShuttle",
  },
  {
    id: "wb-eins-1",
    title: "Fintenkanal",
    ageGroups: MID_OLD, focusAreas: ["eins"], blockType: "warmBall",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Spieler, 2 Hütchen pro Bahn (Abstand 12 m)",
    objective: "Finten automatisieren, Tempowechsel nach der Finte.",
    setup: (n) => `${groupsOf(n, 3)} – pro Gruppe eine Bahn mit Hütchen in der Mitte. Reihum starten.`,
    flow: "Spieler dribbelt auf das mittlere Hütchen zu, zeigt eine Finte (Übersteiger, Schussfinte, Körpertäuschung) und nimmt nach der Finte explosiv Tempo auf. Zurück außen traben.",
    coachingPoints: ["Finte deutlich vor dem Hütchen ansetzen", "Tiefer Körperschwerpunkt", "Explosion nach der Täuschung"],
    coachCommands: ["Tempowechsel!", "Finte verkaufen!", "Explosiv raus!"],
    easierVariation: "Eine feste Finte in Ruhe einüben, Tempo frei.",
    harderVariation: "Trainer zeigt per Handzeichen spät die Seite an – Reaktion + Finte.",
    svgDiagramType: "feintLane",
  },
  {
    id: "wb-fit-1",
    title: "Dribbel-Quadrat mit Belastungsimpulsen",
    ageGroups: MID_OLD, focusAreas: ["fitness", "pass", "eins"], blockType: "warmBall",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Spieler, 4 Hütchen (Feld 20×20 m)",
    objective: "Ballkontrolle unter steigender Belastung, Aktivierung mit Ball.",
    setup: (n) => `Feld 20×20 m, alle ${n} Spieler mit Ball gleichzeitig im Feld.`,
    flow: "Freies Dribbling. Auf Signal: 5 schnelle Sohlenkontakte, Richtungswechsel, kurzer Antritt mit Ball über 5 m, Ball stoppen + 3 Tuckjumps. Belastung in Wellen steuern.",
    coachingPoints: ["Ball auch bei Tempo unter Kontrolle", "Kurze, klare Signale", "Pausen aktiv mit lockerem Dribbling"],
    coachCommands: ["Kopf hoch!", "Antritt – jetzt!", "Ball eng führen!"],
    easierVariation: "Weniger Signale, längere lockere Phasen.",
    harderVariation: "Signale kombinieren, Antritte verlängern, Zweikampf-Schatten dazunehmen.",
    svgDiagramType: "dribbleField",
  },

  /* ---------- Block 4: Erste Spielform ---------- */
  {
    id: "g1-young-pass",
    title: "Inselspiel: Passen auf die Schatzinsel",
    ageGroups: YOUNG, focusAreas: ["pass"], blockType: "game1",
    duration: 15, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Paar, Reifen oder Hütchenquadrate als Inseln",
    objective: "Erste Passgenauigkeit spielerisch entwickeln.",
    setup: (n) => `${groupsOf(n, 2)} – Paare verteilen sich um die „Inseln“ (Reifen) im Feld 20×20 m.`,
    flow: "Paare passen sich den Ball durch eine Insel (Reifen/Hütchentor) zu. Jeder Treffer = 1 Schatz. Nach jedem Treffer neue Insel suchen. Welches Paar sammelt die meisten Schätze?",
    coachingPoints: ["Innenseite zeigen lassen", "Passen aus der Bewegung", "Erfolge laut feiern"],
    coachCommands: ["Mit der Innenseite!", "Sucht euch eine neue Insel!", "Schaut, wo es frei ist!"],
    easierVariation: "Kürzere Abstände, Ball darf zugerollt werden.",
    harderVariation: "Treffer zählt nur mit schwachem Fuß oder direktem Pass.",
    svgDiagramType: "islands",
  },
  {
    id: "g1-young-eins",
    title: "1 gegen 1 auf Hütchentore",
    ageGroups: YOUNG, focusAreas: ["eins"], blockType: "game1",
    duration: 15, minPlayers: 4, maxPlayers: 24,
    material: "Pro Feld 1 Ball, 4 Hütchen (Feld 10×8 m) + 2 Hütchentore",
    objective: "Mut zum Dribbling, Gegner spielerisch ausspielen.",
    setup: (n) => `${groupsOf(n, 4)} – pro Gruppe ein kleines Feld mit 2 Hütchentoren. 2 spielen, 2 pausieren kurz und wechseln fliegend.`,
    flow: "1 gegen 1: Tor erzielen durch Dribbeln durch eines der beiden Hütchentore. Nach max. 30 Sekunden Wechsel. Verteidiger wird nach Ballgewinn sofort Angreifer.",
    coachingPoints: ["Mutig aufs Tor dribbeln", "Tempowechsel nutzen", "Nach Ballgewinn sofort umschalten"],
    coachCommands: ["Mutig ins 1 gegen 1!", "Tempo nach der Finte!", "Ballgewinn – los, andersrum!"],
    easierVariation: "Verteidiger nur halbaktiv, größere Tore.",
    harderVariation: "Nur ein Tor zählt, das der Trainer kurz vorher ansagt.",
    svgDiagramType: "duelGates",
  },
  {
    id: "g1-young-fit",
    title: "Kettenfangen mit Ball",
    ageGroups: YOUNG, focusAreas: ["fitness"], blockType: "game1",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Bälle für alle Läufer, Hütchen für Feld 20×20 m, 2 Leibchen",
    objective: "Schnelligkeit, Ausweichen und Ballkontrolle unter Druck – spielerische Belastung.",
    setup: (n) => `Feld 20×20 m. ${Math.max(1, Math.round(n / 6))} Fänger ohne Ball (Leibchen), alle anderen dribbeln.`,
    flow: "Fänger jagen die Dribbler. Wer abgeschlagen wird, hält den Ball hoch und wird durch „Abklatschen“ eines Mitspielers befreit. Fänger regelmäßig wechseln.",
    coachingPoints: ["Ball auch auf der Flucht eng führen", "Freie Räume suchen", "Fänger oft wechseln – alle sollen sprinten"],
    coachCommands: ["Kopf hoch, Fänger im Blick!", "In den freien Raum!", "Befreit eure Mitspieler!"],
    easierVariation: "Fänger ohne Aufgabe, abgeschlagene Kinder zählen nur Punkte.",
    harderVariation: "Fänger ebenfalls mit Ball; Feld verkleinern.",
    svgDiagramType: "dribbleField",
  },
  {
    id: "g1-old-pass",
    title: "Rondo – Überzahl im Quadrat",
    ageGroups: MID_OLD, focusAreas: ["pass"], blockType: "game1",
    duration: 15, minPlayers: 5, maxPlayers: 24,
    material: "1 Ball pro Rondo (+ Ersatzbälle), 4 Hütchen pro Feld, Leibchen",
    objective: "Passqualität, offene Stellung und schnelles Spiel unter Gegnerdruck.",
    setup: (n) => {
      const rondos = n >= 12 ? Math.round(n / 6) : 1;
      return rondos > 1
        ? `${rondos} Rondos parallel (${groupsOf(n, 6)}), z. B. 4 gegen 2 oder 5 gegen 2 im Feld 8×8 m.`
        : `Ein Rondo ${n - 2} gegen 2 im Feld ${n >= 8 ? "10×10" : "8×8"} m.`;
    },
    flow: "Außenspieler halten den Ball gegen 2 Jäger in der Mitte. Fehlpass oder Ballverlust = Tausch mit dem Jäger. 10 Pässe in Folge = Punkt für das Außenteam.",
    coachingPoints: ["Vor Ballannahme Schulterblick", "Erster Kontakt vom Druck weg", "Passwege durch Bewegung öffnen"],
    coachCommands: ["Kopf hoch!", "Erster Kontakt in Spielrichtung!", "Nach Aktion sofort wieder anbieten!"],
    easierVariation: "Feld vergrößern, Kontaktzahl frei, nur 1 Jäger.",
    harderVariation: "Max. 2 Kontakte, Pflicht-Spielverlagerung nach 5 Pässen (Diagonalpass zählt doppelt).",
    svgDiagramType: "rondo",
  },
  {
    id: "g1-old-eins",
    title: "1 gegen 1 auf zwei Minitore",
    ageGroups: MID_OLD, focusAreas: ["eins"], blockType: "game1",
    duration: 15, minPlayers: 4, maxPlayers: 24,
    material: "Pro Feld: 2 Minitore oder Hütchentore, Bälle, 4 Hütchen (Feld 15×10 m)",
    objective: "Angreifer- und Verteidigerverhalten im direkten Duell.",
    setup: (n) => `${groupsOf(n, 4)} – pro Feld zwei Spieler im Duell, zwei an den Toren als Anspieler/Nachrücker. Fliegender Wechsel.`,
    flow: "Verteidiger passt zum Angreifer (Eröffnungspass) und schiebt heraus. Angreifer sucht das 1 gegen 1 auf eines der zwei Minitore. Nach Ballgewinn darf der Verteidiger kontern.",
    coachingPoints: ["Angreifer: mit Tempo andribbeln, Finte, Richtungswechsel", "Verteidiger: Abstand verkürzen, seitliche Stellung, Timing", "Umschalten sofort nach Ballgewinn/-verlust"],
    coachCommands: ["Mutig ins 1 gegen 1!", "Abstand, seitlich stellen!", "Nach Ballgewinn sofort zum Tor!"],
    easierVariation: "Verteidiger startet später, nur ein Tor verteidigen.",
    harderVariation: "Zeitlimit 8 Sekunden pro Angriff; 1v1 wird nach Pass von außen zum 2v1.",
    svgDiagramType: "duelMinigoals",
  },
  {
    id: "g1-old-fit",
    title: "3 gegen 3 Intervallspiel",
    ageGroups: MID_OLD, focusAreas: ["fitness"], blockType: "game1",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Pro Feld: 2 Minitore, Bälle, Hütchen (Feld 20×15 m), Leibchen",
    objective: "Hohe Intensität in kurzen Intervallen, Belastung über die Spielform steuern.",
    setup: (n) => {
      const fields = Math.max(1, Math.floor(n / 6));
      return `${fields} Feld${fields > 1 ? "er" : ""} 20×15 m, ${teamsLabel(Math.min(n, 6))} pro Feld. Übrige Spieler rotieren nach jedem Intervall ein.`;
    },
    flow: "3 gegen 3 auf Minitore in Intervallen: 90 Sekunden Vollgas, 60 Sekunden aktive Pause (lockeres Passen). 6–8 Durchgänge. Schnelle Ballrückgabe durch Ersatzbälle am Rand.",
    coachingPoints: ["Volle Intensität in der Spielzeit", "Pausen konsequent locker gestalten", "Laufbereitschaft nach Ballverlust einfordern"],
    coachCommands: ["Vollgas – 90 Sekunden!", "Sofort nachsetzen!", "Pause aktiv, locker bleiben!"],
    easierVariation: "Längere Pausen, größeres Feld (weniger Antritte).",
    harderVariation: "Feld verkleinern, Pausen verkürzen, Tore nur nach Tempodribbling über Mittellinie.",
    svgDiagramType: "smallGame",
  },

  /* ---------- Block 5: Übungsblock ---------- */
  {
    id: "d-young-pass",
    title: "Pass-Stationen: Tore-Sammeln zu zweit",
    ageGroups: YOUNG, focusAreas: ["pass"], blockType: "drill",
    duration: 20, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Paar, viele Hütchentore (1,5–2 m breit)",
    objective: "Passgenauigkeit und Mitnahme in einfacher, spielerischer Form.",
    setup: (n) => `${groupsOf(n, 2)} – im Feld 25×25 m stehen ${Math.max(6, Math.round(n * 0.8))} Hütchentore verteilt.`,
    flow: "Paare passen sich den Ball durch wechselnde Hütchentore zu und zählen Treffer. Stufen: 1) frei, 2) nur Innenseite, 3) Mitnahme + Pass durch das nächste Tor, 4) Wettkampf: 2 Minuten, wer hat die meisten Tore?",
    coachingPoints: ["Standbein neben den Ball", "Passstärke dem Abstand anpassen", "Nach dem Pass weiterbewegen"],
    coachCommands: ["Innenseite!", "Nach dem Pass laufen!", "Sucht das freie Tor!"],
    easierVariation: "Tore breiter, Abstände kürzer.",
    harderVariation: "Nur schwacher Fuß, direkter Pass nach Mitnahme, Verbot desselben Tors zweimal in Folge.",
    svgDiagramType: "gatesField",
  },
  {
    id: "d-young-eins",
    title: "Fintenparcours mit Abschluss",
    ageGroups: YOUNG, focusAreas: ["eins"], blockType: "drill",
    duration: 20, minPlayers: 4, maxPlayers: 24,
    material: "1 Ball pro Kind, Hütchen, Stangen oder Markierungen, 1–2 Minitore",
    objective: "Erste Finten kennenlernen und mutig anwenden.",
    setup: (n) => `${groupsOf(n, Math.min(6, Math.max(3, Math.round(n / 3))))} – parallele Parcours-Bahnen, damit keine langen Wartezeiten entstehen.`,
    flow: "Dribbeln durch Slalom, an einem „Geister-Hütchen“ eine Finte zeigen (Schussfinte oder Körpertäuschung), danach Tempodribbling und Abschluss auf das Minitor. Finten gemeinsam vormachen und nachmachen.",
    coachingPoints: ["Finte groß und deutlich", "Nach der Finte schnell werden", "Jedes Kind viele Wiederholungen"],
    coachCommands: ["Trick zeigen!", "Und jetzt schnell!", "Trau dich!"],
    easierVariation: "Ohne Abschluss, Finte in Ruhe am stehenden Hütchen.",
    harderVariation: "Am Ende wartet ein halbaktiver Verteidiger statt des Hütchens.",
    svgDiagramType: "feintLane",
  },
  {
    id: "d-young-fit",
    title: "Bewegungs-Parcours „Dschungel“",
    ageGroups: YOUNG, focusAreas: ["fitness"], blockType: "drill",
    duration: 20, minPlayers: 4, maxPlayers: 24,
    material: "Hütchen, Reifen, Stangen, ggf. kleine Hürden, Bälle",
    objective: "Koordination, Gleichgewicht und Schnelligkeit in spielerischer Form – keine monotone Konditionsarbeit.",
    setup: (n) => `${groupsOf(n, Math.min(6, Math.max(3, Math.round(n / 3))))} – Parcours als Rundkurs mit 4–5 Stationen, mehrere Kinder gleichzeitig unterwegs.`,
    flow: "Stationen: Reifen-Hüpfen (beidbeinig/einbeinig), Slalomlauf, Balancieren auf einer Linie, Krabbeltunnel/Unterqueren, kurzer Sprint ins Ziel. Nach 2 Runden: mit Ball (dribbeln, tragen, rollen).",
    coachingPoints: ["Qualität der Bewegungen loben", "Stationen nach Bedarf anpassen", "Wartezeiten vermeiden"],
    coachCommands: ["Leise landen wie eine Katze!", "Schnelle Füße!", "Gleich bist du dran – fertig machen!"],
    easierVariation: "Weniger Stationen, ohne Ball.",
    harderVariation: "Als Staffelwettkampf zweier Teams.",
    svgDiagramType: "circuit",
  },
  {
    id: "d-mid-pass",
    title: "Passwinkel & offene Stellung (Y-Form)",
    ageGroups: MID, focusAreas: ["pass"], blockType: "drill",
    duration: 20, minPlayers: 6, maxPlayers: 24,
    material: "Pro Gruppe: 4 Hütchen in Y-Form (Abstände 8–10 m), 1–2 Bälle",
    objective: "Passwinkel erkennen, offene Stellung und erster Kontakt in Spielrichtung.",
    setup: (n) => `${groupsOf(n, 6)} – pro Gruppe eine Y-Form. Startposition unten doppelt besetzen.`,
    flow: "Pass von unten ins Zentrum, Zentrumspieler lässt klatschen, Startspieler spielt in eine Y-Spitze, Zentrumspieler läuft entgegen und nimmt offen mit. Positionswechsel dem Ball nach. Nach 6–8 Min Seite/Richtung wechseln.",
    coachingPoints: ["Vor der Annahme lösen und offen stellen", "Passwinkel aktiv herstellen", "Timing: erst Bewegung, dann Pass"],
    coachCommands: ["Offen stehen!", "Erster Kontakt in Spielrichtung!", "Erst lösen, dann fordern!"],
    easierVariation: "Ohne Klatschenlassen, Abstände verkürzen, Kontakte frei.",
    harderVariation: "Max. 2 Kontakte, Tempo erhöhen, zweiter Ball parallel im Umlauf.",
    svgDiagramType: "yShape",
  },
  {
    id: "d-old-pass",
    title: "Positionsspiel mit Spielverlagerung (Doppelquadrat)",
    ageGroups: OLD, focusAreas: ["pass"], blockType: "drill",
    duration: 20, minPlayers: 8, maxPlayers: 24,
    material: "2 verbundene Felder 12×12 m, Leibchen in 3 Farben, Bälle",
    objective: "Ballbesitz sichern, Pressing-Auslöser erkennen, Spielverlagerung in den freien Raum.",
    setup: (n) => {
      const per = Math.floor(n / 2);
      return n >= 14
        ? `2 parallele Doppelquadrate (${groupsOf(n, per)}), z. B. 4 gegen 2 je Feldhälfte.`
        : `Ein Doppelquadrat: ${n - 3} Ballbesitzspieler gegen 3 Presser, Verlagerung ins zweite Feld.`;
    },
    flow: "Ballbesitzteam kombiniert in einem Quadrat gegen Presser. Nach 5 Pässen (oder auf Trainer-Signal) Verlagerung ins zweite Quadrat – Presser sprinten nach. Ballverlust = Rollentausch.",
    coachingPoints: ["Vororientierung vor jedem Kontakt", "Verlagerung vorbereiten (Tiefe + Breite)", "Nach Verlagerung sofort neue Dreiecke bilden"],
    coachCommands: ["Kopf hoch – wo ist es frei?", "Verlagern – jetzt!", "Nach Aktion sofort wieder anbieten!"],
    easierVariation: "Verlagerung erst nach freier Passanzahl, größere Felder.",
    harderVariation: "Max. 2 Kontakte, Verlagerung nur als Diagonalpass, Presser in Überzahl.",
    svgDiagramType: "doubleSquare",
  },
  {
    id: "d-old-eins",
    title: "1 gegen 1: Angreifen & Verteidigen im Detail",
    ageGroups: MID_OLD, focusAreas: ["eins"], blockType: "drill",
    duration: 20, minPlayers: 6, maxPlayers: 24,
    material: "Pro Feld: 1 Jugendtor oder 2 Minitore, Hütchen (Feld 20×15 m), Bälle, Leibchen",
    objective: "Systematisches 1-gegen-1-Verhalten: Andribbeln, Finte, Tempowechsel – Stellung, Abstand, Timing.",
    setup: (n) => `${groupsOf(n, Math.min(8, Math.max(4, Math.round(n / 2))))} – pro Feld zwei Startpositionen (Angreifer-/Verteidigerreihe), Rollen nach jeder Aktion tauschen.`,
    flow: "Phase 1 (8 Min): Verteidiger halbaktiv – Angreifer trainiert Andribbeln mit Tempo, Finte, Durchbruch. Phase 2 (8 Min): Verteidiger aktiv – Fokus auf Herausschieben, seitliche Grundstellung, Timing im Zugriff. Phase 3 (4 Min): freies Duell mit Punktwertung.",
    coachingPoints: ["Angreifer: Gegner anvisieren, Entscheidung vor dem Zugriff", "Verteidiger: Bogenlauf, Tempo aufnehmen, leiten statt hineinspringen", "Nach Ballgewinn sofortiges Umschalten belohnen"],
    coachCommands: ["Mit Tempo andribbeln!", "Seitlich stellen, nicht reinspringen!", "Tempo nach der Aktion!"],
    easierVariation: "Größerer Abstand beim Start, Verteidiger ohne Tackling.",
    harderVariation: "Start aus dem Rücken des Angreifers (Druck von hinten), Zeitlimit 6 Sekunden.",
    svgDiagramType: "duelMinigoals",
  },
  {
    id: "d-old-fit",
    title: "Schnelligkeits- & Stabilisationszirkel",
    ageGroups: MID_OLD, focusAreas: ["fitness"], blockType: "drill",
    duration: 20, minPlayers: 6, maxPlayers: 24,
    material: "Hütchen, Koordinationsleiter (optional), Bälle, Markierungen für 4 Stationen",
    objective: "Antritt, Richtungswechsel, Reaktion und Rumpfstabilität altersgerecht entwickeln.",
    setup: (n) => `${groupsOf(n, Math.ceil(n / 4))} – 4 Stationen, Wechsel alle 4 Minuten (Belastung/Pause innerhalb der Station ca. 1:2).`,
    flow: "Station 1: Reaktionsstarts aus verschiedenen Positionen (5–10 m). Station 2: Richtungswechsel-Parcours mit Ballabschluss. Station 3: Stabilisation (Plank-Varianten, Einbeinstand mit Pass). Station 4: Sprungkoordination + kurzer Sprint.",
    coachingPoints: ["Maximale Qualität bei kurzen Belastungen", "Volle Pausen für echte Schnelligkeit", "Stabi-Übungen sauber statt schnell"],
    coachCommands: ["Erster Schritt explosiv!", "Körperspannung halten!", "Volle Pause – dann wieder 100 %!"],
    easierVariation: "Belastungszeiten verkürzen, Stabi-Übungen vereinfachen.",
    harderVariation: "Reaktionssignale visuell statt akustisch, Sprints mit Ball, Zusatzwiderholung als Wettkampf.",
    svgDiagramType: "circuit",
  },

  /* ---------- Block 6: Zweite Spielform ---------- */
  {
    id: "g2-young-all",
    title: "3 gegen 3 Funino-Spiel",
    ageGroups: YOUNG, focusAreas: ALL_FOCUS, blockType: "game2",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Pro Feld: 4 Minitore/Hütchentore, Hütchen (Feld 25×20 m), Bälle, Leibchen",
    objective: "Viele Aktionen, Entscheidungen und Tore für jedes Kind.",
    setup: (n) => {
      const fields = Math.max(1, Math.floor(n / 6));
      return `${fields} Feld${fields > 1 ? "er" : ""} mit je 2 Toren pro Seite, 3 gegen 3${n % 6 !== 0 ? ", übrige Kinder rotieren fliegend ein" : ""}.`;
    },
    flow: "3 gegen 3 auf je zwei Minitore pro Seite. Schwerpunktregel je nach Fokus: Passspiel = Tor zählt doppelt nach vorherigem Pass; 1 gegen 1 = Tor nach gelungenem Dribbling zählt doppelt; Fitness = nach jedem Tor sprinten beide Teams um ihr Tor herum.",
    coachingPoints: ["Wenig unterbrechen, Kinder spielen lassen", "Beide Tore als Option sehen", "Jubeln ausdrücklich erlaubt"],
    coachCommands: ["Schau, welches Tor frei ist!", "Trau dich!", "Sofort weiterspielen!"],
    easierVariation: "Größeres Feld, keine Zusatzregel.",
    harderVariation: "Torschuss erst nach Überqueren der Mittellinie im Dribbling.",
    svgDiagramType: "funino",
  },
  {
    id: "g2-old-pass",
    title: "4 gegen 4 plus neutrale Spieler",
    ageGroups: MID_OLD, focusAreas: ["pass"], blockType: "game2",
    duration: 15, minPlayers: 8, maxPlayers: 24,
    material: "Feld 30×25 m, 2 Minitore oder Konter-Linien, Leibchen (3 Farben), Bälle",
    objective: "Überzahl im Ballbesitz nutzen: Dreiecke, Doppelpass, Spielverlagerung.",
    setup: (n) => {
      const neutrals = n % 2 === 0 ? Math.min(2, Math.max(0, n - 8)) && 2 : 1;
      const per = Math.floor((n - (n >= 10 ? 2 : n % 2)) / 2);
      return n >= 10
        ? `${per} gegen ${per} plus 2 neutrale Spieler (spielen immer mit dem Ballbesitzteam). Bei ${n} Spielern ggf. zweites Feld aufbauen.`
        : `${teamsLabel(n)} – der Joker spielt immer mit dem Ballbesitzteam.`;
    },
    flow: "Spiel auf Minitore. Pflichtregel: Vor jedem Torabschluss muss ein Doppelpass oder eine Spielverlagerung (Pass über die ganze Feldbreite) erfolgen – sonst zählt das Tor nicht.",
    coachingPoints: ["Neutrale Spieler aktiv einbinden", "Dreiecke um den Ballführenden bilden", "Erst Sicherheit, dann Tiefe suchen"],
    coachCommands: ["Dreieck bilden!", "Spiel verlagern!", "Nach Aktion sofort wieder anbieten!"],
    easierVariation: "Zusatzregel als Bonus (Doppelpunkt) statt Pflicht.",
    harderVariation: "Max. 2 Kontakte für neutrale Spieler, Abseits ab Mittellinie.",
    svgDiagramType: "smallGameNeutral",
  },
  {
    id: "g2-old-eins",
    title: "1v1/2v2-Turnier mit Umschaltmoment",
    ageGroups: MID_OLD, focusAreas: ["eins"], blockType: "game2",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Mehrere Felder 15×12 m mit je 2 Minitoren, Bälle, Leibchen",
    objective: "Duellverhalten unter Wettkampfbedingungen, sofortiges Umschalten.",
    setup: (n) => `${groupsOf(n, 4)} – Turnierform: pro Feld 1v1 oder 2v2, nach jeder Runde Sieger steigen auf („Champions Court“), Verlierer ab.`,
    flow: "Kurze Spiele à 90 Sekunden. Ballgewinn = sofort selbst angreifen. Nach Ablauf rotieren: Gewinner ein Feld hoch, Verlierer eins runter. Punkte zählen über das gesamte Turnier.",
    coachingPoints: ["Duelle annehmen statt ausweichen", "Verteidiger: erst verzögern, dann zugreifen", "Umschalten in beide Richtungen einfordern"],
    coachCommands: ["Mutig ins 1 gegen 1!", "Ballverlust – sofort nachsetzen!", "Erst bremsen, dann zugreifen!"],
    easierVariation: "Längere Pausen zwischen den Runden, 2v2 statt 1v1.",
    harderVariation: "Unterzahl-Runden (1v2 nach Ballverlust), kleinere Felder.",
    svgDiagramType: "duelMinigoals",
  },
  {
    id: "g2-old-fit",
    title: "Umschaltspiel 3 gegen 3 mit Belastungswellen",
    ageGroups: MID_OLD, focusAreas: ["fitness"], blockType: "game2",
    duration: 15, minPlayers: 9, maxPlayers: 24,
    material: "Feld 30×20 m, 2 Tore/Minitore, viele Bälle am Rand, Leibchen (3 Farben)",
    objective: "Wiederholte Sprints und Umschaltaktionen mit gesteuerter Belastung.",
    setup: (n) => {
      const teams = Math.max(3, Math.floor(n / 3));
      return `${teams} Teams à ca. 3 Spieler. Zwei Teams spielen, die übrigen pausieren aktiv und wechseln nach jedem Treffer oder 90 Sekunden ein.`;
    },
    flow: "3 gegen 3 auf zwei Tore. Nach Tor oder Zeitsignal: Verliererteam raus, neues Team sprintet sofort ins Feld und greift an („König bleibt“). Dadurch wechseln sich hohe Belastung und Pausen automatisch ab.",
    coachingPoints: ["Sofortdruck nach Ballverlust", "Einwechselnde Teams starten mit Sprint", "Pausenteams locker in Bewegung halten"],
    coachCommands: ["Neues Team – Vollgas rein!", "Sofort nachsetzen!", "Tempo bis zum Schluss!"],
    easierVariation: "Feste Wechselzeiten statt „Verlierer raus“.",
    harderVariation: "Neues Team startet mit eigenem Ball als Konter – Spiel ohne Unterbrechung.",
    svgDiagramType: "smallGame",
  },

  /* ---------- Spielformen nach „Trainingsphilosophie Deutschland“ (DFB) ---------- */
  {
    id: "g1-tpd-eins",
    title: "2 gegen 2 in 8 Sekunden (DFB-Spielform)",
    ageGroups: MID_OLD, focusAreas: ["eins", "fitness"], blockType: "game1",
    duration: 15, minPlayers: 8, maxPlayers: 24,
    material: "Feld 25×20 m, 2 Tore mit Torhütern (oder Minitore), viele Bälle am Rand",
    objective: "Zielstrebigkeit zum Tor, viele Zweikämpfe, hohe Aktionsdichte unter Zeitdruck.",
    setup: (n) => `2 Teams à ${Math.floor(n / 2)} Spieler neben den Toren verteilt. Immer 2 gegen 2 im Feld, Rest wartet kurz und startet sofort nach – fliegender Wechsel.`,
    flow: "Trainer spielt zu einem Angreiferpaar ein und zählt laut von 8 herunter. Innerhalb der 8 Sekunden muss abgeschlossen werden. Treffer oder Zeitablauf beendet den Durchgang, das nächste Paar startet sofort. Bei Ballverlust kontern die Verteidiger direkt.",
    coachingPoints: ["Sofort nach vorn denken", "Mutig ins gegnerüberwindende Dribbling", "Mitspieler nutzen, wenn er besser steht"],
    coachCommands: ["8 – 7 – 6 …!", "Zum Tor – jetzt!", "Mutig ins 1 gegen 1!"],
    easierVariation: "10–12 Sekunden Zeit, größeres Feld.",
    harderVariation: "Treffer nur per Direktabschluss, Konter zählt doppelt.",
    svgDiagramType: "smallGame",
  },
  {
    id: "g2-tpd-dreh",
    title: "3 gegen 3 mit drehendem Angriffsrecht (DFB-Spielform)",
    ageGroups: MID_OLD, focusAreas: ["eins", "pass", "fitness"], blockType: "game2",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Pro Feld 20×20 m: 1 Tor mit Torhüter, 2 Minitore, Balldepot",
    objective: "Schnelles Umschalten in beide Richtungen, Duelle mit Zug zum Tor.",
    setup: (n) => {
      const fields = Math.max(1, Math.floor(n / 7));
      return `${fields} Hybridfeld${fields > 1 ? "er" : ""}: je 3 gegen 3 (+ Torhüter). Übrige Spieler rotieren nach jedem Durchgang ein.`;
    },
    flow: "Ein Team greift auf die Minitore an. Nach einem Treffer dreht das Angriffsrecht: Das erfolgreiche Team darf auf das große Tor mit Torhüter angreifen. Erobern die Verteidiger den Ball, kontern sie sofort auf die Minitore, um ihrerseits das Angriffsrecht zu gewinnen.",
    coachingPoints: ["Ballgewinn = sofort umschalten", "Beide Zielrichtungen ständig im Kopf", "Hohes Tempo, wenig Unterbrechungen"],
    coachCommands: ["Angriffsrecht – dreht!", "Sofort kontern!", "Nach Aktion sofort wieder anbieten!"],
    easierVariation: "Ohne Drehrecht: feste Angriffsrichtung, nach Zeit wechseln.",
    harderVariation: "Shotclock 10 Sekunden pro Angriff, mit Abseits ab Mittellinie.",
    svgDiagramType: "duelMinigoals",
  },
  {
    id: "g2-tpd-linie",
    title: "4 gegen 4 – eine Linie verteidigen (DFB-Spielform)",
    ageGroups: OLD, focusAreas: ["pass", "eins"], blockType: "game2",
    duration: 15, minPlayers: 8, maxPlayers: 24,
    material: "Doppelter Strafraum, Mittellinie, 1 Tor mit Torhüter, 2–3 Minitore, Balldepot",
    objective: "Tiefe bedrohen und bespielen (offensiv); Verschieben, Herausrücken, Absichern auf einer Linie (defensiv).",
    setup: (n) => `${Math.max(1, Math.floor(n / 8))} Feld(er): 4 gegen 4, Verteidiger organisieren sich als Kette an der Mittellinie. Übrige Spieler wechseln nach jedem Durchgang.`,
    flow: "Mit Abseits an der Mittellinie. Die Viererkette verteidigt auf der Linie, nur ein Spieler darf herausrücken. Angreifer binden Gegner und attackieren die Tiefe mit und ohne Ball. Nach Ballgewinn der Kette: 30 Sekunden freies Spiel auf die Minitore.",
    coachingPoints: ["Kette: verschieben, übergeben/übernehmen, kommunizieren", "Nur einer rückt heraus, Rest sichert", "Offensiv: Tiefenläufe im richtigen Moment"],
    coachCommands: ["Linie halten!", "Einer raus – Rest sichern!", "Jetzt die Tiefe!"],
    easierVariation: "Ohne Abseits, Verteidiger dürfen die Linie früher verlassen.",
    harderVariation: "Abseitslinie höher schieben (mehr Raum im Rücken), Konterzeit verkürzen.",
    svgDiagramType: "smallGame",
  },
  {
    id: "g1-tpd-funino",
    title: "Funino 3 gegen 3 (DFB-Spielform)",
    ageGroups: MID_OLD, focusAreas: ["eins", "pass"], blockType: "game1",
    duration: 15, minPlayers: 6, maxPlayers: 24,
    material: "Pro Feld 20×18 m: 4 Minitore, zwei 5 m tiefe Abschlusszonen, Balldepots zwischen den Toren",
    objective: "Maximale Aktionsdichte: Dribbling, 1 gegen 1, Abschlüsse, Pressing und Gegenpressing.",
    setup: (n) => {
      const fields = Math.max(1, Math.floor(n / 6));
      return `${fields} Funino-Feld${fields > 1 ? "er" : ""} parallel, je 3 gegen 3. Treffer zählen nur aus der Abschlusszone. Bälle liegen bereit – sofortige Spielfortsetzung.`;
    },
    flow: "Freies 3 gegen 3 auf je zwei Minitore. Geht der Ball ins Aus, sofort neuer Ball aus dem Depot – der Spielfluss bleibt hoch. Mehrere Felder im Champions-League-Modus: Sieger steigen auf, Verlierer ab.",
    coachingPoints: ["Spielfluss schützen – sofort neuer Ball", "Beide Tore als Option lesen", "Positiv und emotional begleiten, wenig Detailcoaching"],
    coachCommands: ["Weiterspielen!", "Schau, welches Tor frei ist!", "Sofort nachsetzen!"],
    easierVariation: "Ohne Abschlusszonen spielen.",
    harderVariation: "Mit Abseits oder: Treffer zählen nur in der gegnerischen Hälfte.",
    svgDiagramType: "funino",
  },
  {
    id: "f-all",
    title: "Freies Abschlussspiel mit Schwerpunktregel",
    ageGroups: ALL_AGES, focusAreas: ALL_FOCUS, blockType: "final",
    duration: 10, minPlayers: 4, maxPlayers: 24,
    material: "2 Tore (Größe je nach Jugend), Leibchen, Bälle, Hütchen für Feldgröße",
    objective: "Freies Spielen, Gelerntes anwenden, positiver Trainingsabschluss.",
    setup: (n) => `${teamsLabel(n)} auf feldgerechter Größe (Faustregel: ca. 10 m Feldlänge pro Spieler einer Mannschaft).`,
    flow: "Freies Spiel mit genau einer Zusatzregel passend zum Schwerpunkt. Trainer coacht nur in natürlichen Pausen – die Kinder sollen frei Fußball spielen.",
    coachingPoints: ["Wenig eingreifen, Spielfluss schützen", "Schwerpunktaktionen kurz und laut loben", "Mit Erfolgserlebnis enden"],
    coachCommands: ["Frei spielen!", "Stark – genau so!", "Letzte Aktion – alles geben!"],
    easierVariation: "Ganz ohne Zusatzregel spielen lassen.",
    harderVariation: "Zusatzregel verschärfen (z. B. Punkt nur bei erfüllter Schwerpunktaktion).",
    svgDiagramType: "finalGame",
  },
];

const FINAL_RULES = {
  pass: "Zusatzregel Passspiel: Ein Tor zählt doppelt, wenn vorher mindestens 5 Pässe in Folge (jüngere: 3 Pässe) gelingen.",
  eins: "Zusatzregel 1 gegen 1: Ein Tor nach gewonnenem Dribbling/Duell zählt doppelt.",
  fitness: "Zusatzregel Fitness: Nach jedem Tor laufen beide Teams einmal um ihr eigenes Tor, das Spiel läuft sofort weiter.",
};

/* ====================== src/utils/generateTrainingPlan.ts ================= */
function getPool(blockType, age, focus, players) {
  const matches = (ex) =>
    ex.blockType === blockType &&
    ex.ageGroups.includes(age) &&
    players >= ex.minPlayers &&
    players <= ex.maxPlayers;

  let pool = EXERCISES.filter((ex) => matches(ex) && ex.focusAreas.includes(focus));
  if (pool.length === 0) pool = EXERCISES.filter(matches); // Fallback: blockpassend, fokus-neutral
  if (pool.length === 0) pool = EXERCISES.filter((ex) => ex.blockType === blockType && ex.ageGroups.includes(age));
  return pool;
}

function generateTrainingPlan(age, focus, players, totalMinutes, seeds) {
  const blocks = scaleBlocks(totalMinutes);
  return blocks.map((block, i) => {
    const pool = getPool(block.type, age, focus, players);
    const exercise = pool.length ? pool[seeds[i] % pool.length] : null;
    return { block, exercise, alternatives: pool.length };
  });
}

/* ====================== src/components/ExerciseDiagram.tsx ================ */
const C = {
  pitch: "#2f8a4d",
  line: "rgba(255,255,255,0.85)",
  teamA: "#fbbf24", // gelb
  teamB: "#ffffff",
  neutral: "#60a5fa",
  cone: "#fb923c",
  ball: "#111827",
};

const Player = ({ x, y, fill = C.teamA, label }) => (
  <g>
    <circle cx={x} cy={y} r="9" fill={fill} stroke="rgba(0,0,0,0.35)" strokeWidth="1.5" />
    {label && (
      <text x={x} y={y + 3.5} textAnchor="middle" fontSize="9" fontWeight="700" fill="#1f2937">
        {label}
      </text>
    )}
  </g>
);
const Cone = ({ x, y }) => <path d={`M ${x} ${y - 7} L ${x + 6} ${y + 5} L ${x - 6} ${y + 5} Z`} fill={C.cone} stroke="rgba(0,0,0,0.3)" strokeWidth="1" />;
const Ball = ({ x, y }) => (
  <g>
    <circle cx={x} cy={y} r="4.5" fill="#fff" stroke={C.ball} strokeWidth="1.5" />
    <circle cx={x} cy={y} r="1.6" fill={C.ball} />
  </g>
);
const Goal = ({ x, y, w = 36, vertical = false }) =>
  vertical ? (
    <rect x={x - 4} y={y - w / 2} width="8" height={w} fill="none" stroke="#fff" strokeWidth="3" />
  ) : (
    <rect x={x - w / 2} y={y - 4} width={w} height="8" fill="none" stroke="#fff" strokeWidth="3" />
  );
const Arrow = ({ x1, y1, x2, y2, dashed = false }) => {
  const ang = Math.atan2(y2 - y1, x2 - x1);
  const ah = 7;
  return (
    <g stroke="#fff" strokeWidth="2" fill="#fff" opacity="0.95">
      <line x1={x1} y1={y1} x2={x2} y2={y2} strokeDasharray={dashed ? "5 4" : "none"} />
      <path d={`M ${x2} ${y2} L ${x2 - ah * Math.cos(ang - 0.45)} ${y2 - ah * Math.sin(ang - 0.45)} L ${x2 - ah * Math.cos(ang + 0.45)} ${y2 - ah * Math.sin(ang + 0.45)} Z`} />
    </g>
  );
};

function ExerciseDiagram({ type, players }) {
  const W = 340, H = 210;
  const Pitch = ({ children }) => (
    <svg viewBox={`0 0 ${W} ${H}`} className="w-full rounded-xl" role="img" aria-label="Übungsskizze">
      <rect width={W} height={H} rx="12" fill={C.pitch} />
      <rect x="14" y="14" width={W - 28} height={H - 28} fill="none" stroke={C.line} strokeWidth="2" rx="4" />
      {children}
    </svg>
  );

  const many = players >= 12;

  switch (type) {
    case "freeArea":
      return (
        <Pitch>
          {[ [70,60],[140,110],[220,55],[260,140],[110,160],[185,150],[250,90],[90,105] ].slice(0, many ? 8 : 5)
            .map(([x, y], i) => <Player key={i} x={x} y={y} fill={i % 2 ? C.teamB : C.teamA} />)}
          <Arrow x1={70} y1={60} x2={120} y2={45} dashed />
          <Arrow x1={220} y1={55} x2={245} y2={100} dashed />
          <Arrow x1={110} y1={160} x2={160} y2={170} dashed />
        </Pitch>
      );
    case "lanes":
      return (
        <Pitch>
          {[60, 105, 150].map((y) => (
            <g key={y}>
              <Cone x={50} y={y} /><Cone x={290} y={y} />
              <line x1={60} y1={y} x2={280} y2={y} stroke="rgba(255,255,255,0.35)" strokeDasharray="3 5" />
            </g>
          ))}
          <Player x={50} y={172} /><Player x={75} y={172} fill={C.teamB} />{many && <Player x={100} y={172} />}
          <Arrow x1={60} y1={60} x2={150} y2={60} dashed />
          <Arrow x1={60} y1={105} x2={150} y2={105} dashed />
        </Pitch>
      );
    case "dribbleField":
      return (
        <Pitch>
          {[[28,28],[312,28],[28,182],[312,182]].map(([x,y],i)=><Cone key={i} x={x} y={y}/>)}
          {[ [80,70],[150,120],[230,60],[260,150],[120,160],[200,105] ].slice(0, many ? 6 : 4).map(([x, y], i) => (
            <g key={i}><Player x={x} y={y} /><Ball x={x + 12} y={y + 9} /></g>
          ))}
          <Arrow x1={80} y1={70} x2={125} y2={90} dashed />
          <Arrow x1={230} y1={60} x2={250} y2={110} dashed />
        </Pitch>
      );
    case "passShuttle":
      return (
        <Pitch>
          <Cone x={70} y={105} /><Cone x={270} y={105} />
          <Player x={70} y={130} label="A" /><Player x={95} y={130} fill={C.teamB} label="C" />
          <Player x={270} y={130} label="B" />
          <Ball x={86} y={118} />
          <Arrow x1={95} y1={118} x2={255} y2={118} />
          <Arrow x1={75} y1={140} x2={245} y2={150} dashed />
        </Pitch>
      );
    case "feintLane":
      return (
        <Pitch>
          <Cone x={170} y={105} />
          <Player x={55} y={105} /><Ball x={68} y={112} />
          {many && <Player x={40} y={140} fill={C.teamA} />}
          <Arrow x1={70} y1={105} x2={150} y2={105} dashed />
          <Arrow x1={185} y1={95} x2={265} y2={70} dashed />
          <Goal x={300} y={62} w={30} vertical />
          <text x={170} y={135} textAnchor="middle" fontSize="11" fill="#fff" fontWeight="600">Finte</text>
        </Pitch>
      );
    case "islands":
      return (
        <Pitch>
          {[[120,70],[230,120],[160,160]].map(([x,y],i)=>(
            <circle key={i} cx={x} cy={y} r="16" fill="none" stroke="#fbbf24" strokeWidth="3" />
          ))}
          <Player x={60} y={70} /><Player x={180} y={70} fill={C.teamB} />
          <Ball x={78} y={70} />
          <Arrow x1={85} y1={70} x2={165} y2={70} />
        </Pitch>
      );
    case "duelGates":
    case "duelMinigoals":
      return (
        <Pitch>
          {type === "duelGates" ? (
            <g><Cone x={250} y={55} /><Cone x={250} y={90} /><Cone x={250} y={130} /><Cone x={250} y={165} /></g>
          ) : (
            <g><Goal x={300} y={70} w={34} vertical /><Goal x={300} y={150} w={34} vertical /></g>
          )}
          <Player x={80} y={110} label="A" /><Ball x={94} y={118} />
          <Player x={160} y={110} fill={C.teamB} label="V" />
          {many && <g><Player x={50} y={170} /><Player x={50} y={50} fill={C.teamB} /></g>}
          <Arrow x1={100} y1={105} x2={140} y2={90} dashed />
          <Arrow x1={150} y1={85} x2={240} y2={70} dashed />
        </Pitch>
      );
    case "rondo":
      return (
        <Pitch>
          {[[60,40],[280,40],[60,170],[280,170]].map(([x,y],i)=><Cone key={i} x={x} y={y}/>)}
          {[[170,38],[58,105],[282,105],[170,172],[110,40],[230,172]].slice(0, many ? 6 : 4)
            .map(([x,y],i)=><Player key={i} x={x} y={y} />)}
          <Player x={145} y={100} fill={C.teamB} /><Player x={195} y={115} fill={C.teamB} />
          <Ball x={170} y={50} />
          <Arrow x1={160} y1={50} x2={72} y2={96} />
          <Arrow x1={70} y1={115} x2={158} y2={165} />
        </Pitch>
      );
    case "yShape":
      return (
        <Pitch>
          <Cone x={60} y={170} /><Cone x={170} y={110} /><Cone x={260} y={50} /><Cone x={260} y={165} />
          <Player x={60} y={155} label="A" /><Ball x={74} y={162} />
          <Player x={170} y={95} fill={C.teamB} label="B" />
          <Player x={260} y={35} label="C" /><Player x={260} y={150} label="D" />
          <Arrow x1={75} y1={150} x2={155} y2={105} />
          <Arrow x1={185} y1={90} x2={245} y2={50} />
          <Arrow x1={175} y1={110} x2={240} y2={145} dashed />
        </Pitch>
      );
    case "doubleSquare":
      return (
        <Pitch>
          <rect x="30" y="40" width="125" height="130" fill="none" stroke="#fff" strokeWidth="2" strokeDasharray="6 4" />
          <rect x="185" y="40" width="125" height="130" fill="none" stroke="#fff" strokeWidth="2" strokeDasharray="6 4" />
          {[[45,55],[140,55],[45,155],[140,155]].map(([x,y],i)=><Player key={i} x={x} y={y} />)}
          <Player x={80} y={105} fill={C.teamB} /><Player x={115} y={105} fill={C.teamB} />
          <Ball x={58} y={60} />
          <Arrow x1={150} y1={60} x2={230} y2={60} />
          <Player x={230} y={70} fill={C.neutral} />
        </Pitch>
      );
    case "gatesField":
      return (
        <Pitch>
          {[[100,60],[100,85],[210,120],[210,145],[160,40],[185,40],[120,160],[145,160]].map(([x,y],i)=><Cone key={i} x={x} y={y}/>)}
          <Player x={55} y={72} /><Player x={150} y={72} fill={C.teamB} />
          <Ball x={70} y={72} />
          <Arrow x1={78} y1={72} x2={138} y2={72} />
          <Arrow x1={160} y1={80} x2={195} y2={125} dashed />
        </Pitch>
      );
    case "circuit":
      return (
        <Pitch>
          {[[60,55],[100,55],[140,55]].map(([x,y],i)=><Cone key={i} x={x} y={y}/>)}
          {[[210,50],[245,50]].map(([x,y],i)=><circle key={i} cx={x} cy={y} r="12" fill="none" stroke="#fbbf24" strokeWidth="3" />)}
          <line x1="60" y1="150" x2="160" y2="150" stroke="#fff" strokeWidth="3" />
          <Player x={40} y={100} /><Ball x={52} y={108} />
          <Arrow x1={55} y1={70} x2={140} y2={70} dashed />
          <Arrow x1={160} y1={62} x2={205} y2={58} dashed />
          <Arrow x1={250} y1={65} x2={280} y2={130} dashed />
          <Arrow x1={270} y1={150} x2={175} y2={155} dashed />
        </Pitch>
      );
    case "smallGame":
    case "smallGameNeutral":
    case "funino":
    case "finalGame": {
      const isFunino = type === "funino";
      return (
        <Pitch>
          {isFunino ? (
            <g>
              <Goal x={28} y={70} w={30} vertical /><Goal x={28} y={150} w={30} vertical />
              <Goal x={312} y={70} w={30} vertical /><Goal x={312} y={150} w={30} vertical />
            </g>
          ) : (
            <g><Goal x={24} y={105} w={44} vertical /><Goal x={316} y={105} w={44} vertical /></g>
          )}
          <line x1={170} y1={16} x2={170} y2={194} stroke="rgba(255,255,255,0.4)" strokeWidth="2" />
          {[[75,70],[110,130],[140,80]].map(([x,y],i)=><Player key={i} x={x} y={y} />)}
          {[[230,70],[200,130],[265,120]].map(([x,y],i)=><Player key={i} x={x} y={y} fill={C.teamB} />)}
          {many && <g><Player x={75} y={170} /><Player x={265} y={50} fill={C.teamB} /></g>}
          {type === "smallGameNeutral" && <g><Player x={170} y={40} fill={C.neutral} label="N" /><Player x={170} y={170} fill={C.neutral} label="N" /></g>}
          <Ball x={125} y={92} />
          <Arrow x1={133} y1={90} x2={195} y2={122} />
          <Arrow x1={140} y1={70} x2={175} y2={55} dashed />
        </Pitch>
      );
    }
    default:
      return null;
  }
}

/* ====================== src/components/Header.tsx ========================= */
function ClubLogo() {
  // Stilisierte SVG-Nachbildung des SVS-Wappens (schwarz/weiß, Diagonalband).
  // Lokal kann hier alternativ <img src="/logo.png" /> eingesetzt werden.
  return (
    <svg viewBox="0 0 60 64" className="h-11 w-auto" aria-label="SV Schöning 1926 Wappen">
      <defs>
        <clipPath id="svsShield">
          <path d="M30 4 C22 8 12 9 5 8 C4 22 4 38 9 47 C14 55 23 60 30 62 C37 60 46 55 51 47 C56 38 56 22 55 8 C48 9 38 8 30 4 Z" />
        </clipPath>
      </defs>
      <path d="M30 2 C22 6.5 11 8 3 6.5 C2 22 2 39 7.5 48.5 C13 57 23 61.5 30 63.5 C37 61.5 47 57 52.5 48.5 C58 39 58 22 57 6.5 C49 8 38 6.5 30 2 Z" fill="#0a0a0a" />
      <path d="M30 5.5 C23 9 13.5 10.3 6.5 9.3 C5.8 22.5 6 37.5 10.8 46 C15.6 53.5 24 57.8 30 59.7 C36 57.8 44.4 53.5 49.2 46 C54 37.5 54.2 22.5 53.5 9.3 C46.5 10.3 37 9 30 5.5 Z" fill="#ffffff" />
      <g clipPath="url(#svsShield)">
        <rect x="-14" y="24" width="92" height="13" fill="#0a0a0a" transform="rotate(-32 30 32)" />
      </g>
      <text x="-1" y="6" transform="rotate(-32 30 32)" fontSize="9.5" fontWeight="800" letterSpacing="1" fill="#ffffff" fontFamily="system-ui" textAnchor="start">
        <tspan x="9" y="35.5">SCHÖNING</tspan>
      </text>
      <text x="17" y="19" fontSize="10" fontWeight="800" fill="#0a0a0a" fontFamily="system-ui">SV</text>
      <text x="29" y="53" fontSize="9" fontWeight="800" fill="#0a0a0a" fontFamily="system-ui">1926</text>
    </svg>
  );
}

function Header() {
  return (
    <header className="bg-neutral-950 text-white">
      <div className="mx-auto flex max-w-2xl items-center gap-3 px-4 py-3">
        <ClubLogo />
        <div>
          <h1 className="text-lg font-bold leading-tight tracking-tight">Trainingsplaner</h1>
          <p className="text-xs font-medium uppercase tracking-widest text-neutral-400">SV Schöning</p>
        </div>
      </div>
    </header>
  );
}

/* ====================== src/components/TrainingConfigurator.tsx =========== */
function Stepper({ value, onChange, min, max }) {
  return (
    <div className="flex items-center gap-3">
      <button
        onClick={() => onChange(Math.max(min, value - 1))}
        className="h-11 w-11 rounded-xl bg-neutral-100 text-xl font-bold text-neutral-800 active:bg-neutral-200"
        aria-label="Spieler entfernen"
      >−</button>
      <div className="min-w-[3.5rem] text-center">
        <div className="text-2xl font-extrabold text-slate-900">{value}</div>
        <div className="text-[11px] uppercase tracking-wide text-slate-500">Spieler</div>
      </div>
      <button
        onClick={() => onChange(Math.min(max, value + 1))}
        className="h-11 w-11 rounded-xl bg-neutral-100 text-xl font-bold text-neutral-800 active:bg-neutral-200"
        aria-label="Spieler hinzufügen"
      >+</button>
      <input
        type="range" min={min} max={max} value={value}
        onChange={(e) => onChange(Number(e.target.value))}
        className="ml-1 w-full accent-black"
        aria-label="Spieleranzahl"
      />
    </div>
  );
}

function TrainingConfigurator({ age, setAge, focus, setFocus, players, setPlayers, duration, setDuration, onGenerate, onVariant, hasPlan }) {
  const selectCls =
    "w-full rounded-xl border border-slate-200 bg-white px-3 py-3 text-base font-medium text-slate-900 focus:border-neutral-900 focus:outline-none";
  return (
    <section className="rounded-2xl bg-white p-4 shadow-sm ring-1 ring-slate-100">
      <div className="grid grid-cols-1 gap-3 sm:grid-cols-2">
        <label className="block">
          <span className="mb-1 block text-xs font-semibold uppercase tracking-wide text-slate-500">Jugendmannschaft</span>
          <select value={age} onChange={(e) => setAge(e.target.value)} className={selectCls}>
            {AGE_GROUPS.map((a) => <option key={a} value={a}>{a}</option>)}
          </select>
        </label>
        <label className="block">
          <span className="mb-1 block text-xs font-semibold uppercase tracking-wide text-slate-500">Trainingsschwerpunkt</span>
          <select value={focus} onChange={(e) => setFocus(e.target.value)} className={selectCls}>
            {FOCUS_OPTIONS.map((f) => <option key={f.value} value={f.value}>{f.label}</option>)}
          </select>
        </label>
      </div>
      <div className="mt-4">
        <span className="mb-1 block text-xs font-semibold uppercase tracking-wide text-slate-500">Spieleranzahl (4–24)</span>
        <Stepper value={players} onChange={setPlayers} min={4} max={24} />
      </div>
      <div className="mt-4">
        <div className="mb-1 flex items-baseline justify-between">
          <span className="text-xs font-semibold uppercase tracking-wide text-slate-500">Trainingsdauer (45–120 Min)</span>
          <span className="text-sm font-extrabold text-slate-900">{duration} Min</span>
        </div>
        <input
          type="range" min={45} max={120} step={5} value={duration}
          onChange={(e) => setDuration(Number(e.target.value))}
          className="w-full accent-black"
          aria-label="Trainingsdauer in Minuten"
        />
      </div>
      <div className="mt-4 flex gap-2">
        <button
          onClick={onGenerate}
          className="flex-1 rounded-xl bg-neutral-900 px-4 py-3.5 text-base font-bold text-white shadow-sm active:bg-neutral-950"
        >
          Training generieren
        </button>
        {hasPlan && (
          <button
            onClick={onVariant}
            className="rounded-xl border border-neutral-900 px-4 py-3.5 text-sm font-bold text-neutral-800 active:bg-neutral-100"
          >
            Neue Variante
          </button>
        )}
      </div>
    </section>
  );
}

/* ====================== src/components/TrainingBlockCard.tsx ============== */
function InfoRow({ label, children }) {
  return (
    <div>
      <div className="text-[11px] font-semibold uppercase tracking-wide text-slate-500">{label}</div>
      <div className="mt-0.5 text-sm leading-relaxed text-slate-800">{children}</div>
    </div>
  );
}

function TrainingBlockCard({ block, exercise, players, focus, defaultOpen, onSwap, alternatives }) {
  const [open, setOpen] = useState(defaultOpen);
  if (!exercise) return null;
  const isFinal = exercise.blockType === "final";

  return (
    <article className="overflow-hidden rounded-2xl bg-white shadow-sm ring-1 ring-slate-100">
      <button onClick={() => setOpen((o) => !o)} className="flex w-full items-start gap-3 px-4 py-3.5 text-left">
        <div className="flex-1">
          <div className="text-[11px] font-semibold uppercase tracking-wide text-neutral-600">{block.label}</div>
          <h3 className="mt-0.5 text-base font-bold leading-snug text-slate-900">{exercise.title}</h3>
          <p className="mt-1 text-sm text-slate-600">{exercise.objective}</p>
        </div>
        <div className="flex flex-col items-end gap-1">
          <span className="rounded-full bg-neutral-100 px-2.5 py-1 text-xs font-bold text-neutral-800">{block.duration} Min</span>
          <span className={`text-slate-400 transition-transform ${open ? "rotate-180" : ""}`} aria-hidden>▾</span>
        </div>
      </button>

      {open && (
        <div className="space-y-4 border-t border-slate-100 px-4 pb-4 pt-3">
          <ExerciseDiagram type={exercise.svgDiagramType} players={players} />
          <InfoRow label="Organisation">{exercise.setup(players)}</InfoRow>
          <InfoRow label="Material">{exercise.material}</InfoRow>
          <InfoRow label="Ablauf">
            {exercise.flow}
            {isFinal && <span className="mt-1 block font-medium text-neutral-800">{FINAL_RULES[focus]}</span>}
          </InfoRow>

          <div className="rounded-xl bg-neutral-100 p-3">
            <div className="text-[11px] font-semibold uppercase tracking-wide text-neutral-800">Coaching-Schwerpunkte</div>
            <ul className="mt-1.5 space-y-1">
              {exercise.coachingPoints.map((p, i) => (
                <li key={i} className="flex gap-2 text-sm text-neutral-900"><span aria-hidden>•</span>{p}</li>
              ))}
            </ul>
            <div className="mt-3 flex flex-wrap gap-1.5">
              {exercise.coachCommands.map((c, i) => (
                <span key={i} className="rounded-full bg-neutral-900 px-2.5 py-1 text-xs font-semibold text-white">„{c}“</span>
              ))}
            </div>
          </div>

          <div className="grid grid-cols-1 gap-3 sm:grid-cols-2">
            <InfoRow label="Einfacher machen">{exercise.easierVariation}</InfoRow>
            <InfoRow label="Schwerer machen">{exercise.harderVariation}</InfoRow>
          </div>

          <button
            onClick={onSwap}
            disabled={alternatives < 2}
            className="w-full rounded-xl border border-neutral-300 px-3 py-2.5 text-sm font-bold text-neutral-900 active:bg-neutral-100 disabled:opacity-40"
          >
            ⇄ Übung tauschen {alternatives > 1 ? `(${alternatives} Varianten)` : "(keine Alternative)"}
          </button>
        </div>
      )}
    </article>
  );
}

/* ====================== src/components/TrainingPlan.tsx =================== */
function TrainingPlan({ plan, players, focus, age, duration, onSwapBlock, onExportPdf }) {
  const focusLabel = FOCUS_OPTIONS.find((f) => f.value === focus)?.label;
  return (
    <section className="space-y-3">
      <div className="flex items-baseline justify-between px-1">
        <h2 className="text-sm font-bold text-slate-900">
          {age} · {focusLabel} · {players} Spieler
        </h2>
        <span className="text-xs font-medium text-slate-500">{duration} Minuten</span>
      </div>
      {plan.map(({ block, exercise, alternatives }, i) => (
        <TrainingBlockCard
          key={block.type + (exercise?.id ?? i)}
          block={block}
          exercise={exercise}
          players={players}
          focus={focus}
          defaultOpen={i === 0}
          alternatives={alternatives}
          onSwap={() => onSwapBlock(i)}
        />
      ))}
      <button
        onClick={onExportPdf}
        className="w-full rounded-xl bg-neutral-900 px-4 py-3.5 text-base font-bold text-white shadow-sm active:bg-black"
      >
        ⬇ Trainingseinheit als PDF erstellen
      </button>
      <p className="px-1 text-center text-[11px] leading-relaxed text-slate-400">
        Es öffnet sich der Druckdialog — dort „Als PDF speichern“ wählen. Der vorgeschlagene
        Dateiname enthält Jugend, Schwerpunkt, Spieleranzahl, Dauer und Datum.
      </p>
    </section>
  );
}

/* ====================== src/components/PrintView.tsx ======================
   Nur im Druck sichtbar: vollständiger Plan inkl. aller Details & Grafiken. */
function PrintView({ plan, config, duration }) {
  const focusLabel = FOCUS_OPTIONS.find((f) => f.value === config.focus)?.label;
  return (
    <div className="print-only">
      <div style={{ fontFamily: "system-ui", color: "#111" }}>
        <div style={{ display: "flex", alignItems: "center", gap: 12, borderBottom: "3px solid #000", paddingBottom: 10, marginBottom: 14 }}>
          <ClubLogo />
          <div>
            <div style={{ fontSize: 20, fontWeight: 800 }}>Trainingsplaner SV Schöning</div>
            <div style={{ fontSize: 13 }}>
              {config.age} · Schwerpunkt {focusLabel} · {config.players} Spieler · {duration} Minuten · {new Date().toLocaleDateString("de-DE")}
            </div>
          </div>
        </div>
        {plan.map(({ block, exercise }) =>
          exercise ? (
            <div key={block.type} style={{ pageBreakInside: "avoid", border: "1px solid #ccc", borderRadius: 10, padding: 12, marginBottom: 10 }}>
              <div style={{ fontSize: 10, textTransform: "uppercase", letterSpacing: 1, fontWeight: 700 }}>
                {block.label} · {block.duration} Min
              </div>
              <div style={{ fontSize: 15, fontWeight: 800, margin: "2px 0 6px" }}>{exercise.title}</div>
              <div style={{ display: "flex", gap: 12 }}>
                <div style={{ width: 230, flexShrink: 0 }}>
                  <ExerciseDiagram type={exercise.svgDiagramType} players={config.players} />
                </div>
                <div style={{ fontSize: 11, lineHeight: 1.45 }}>
                  <p><b>Ziel:</b> {exercise.objective}</p>
                  <p><b>Organisation:</b> {exercise.setup(config.players)}</p>
                  <p><b>Material:</b> {exercise.material}</p>
                  <p><b>Ablauf:</b> {exercise.flow}{exercise.blockType === "final" ? " " + FINAL_RULES[config.focus] : ""}</p>
                  <p><b>Coaching:</b> {exercise.coachingPoints.join(" · ")}</p>
                  <p><b>Kommandos:</b> {exercise.coachCommands.map((c) => `„${c}“`).join(" ")}</p>
                  <p><b>Einfacher:</b> {exercise.easierVariation} <b>Schwerer:</b> {exercise.harderVariation}</p>
                </div>
              </div>
            </div>
          ) : null
        )}
      </div>
    </div>
  );
}

/* ====================== src/App.tsx ======================================= */
export default function App() {
  const [age, setAge] = useState("D-Jugend");
  const [focus, setFocus] = useState("pass");
  const [players, setPlayers] = useState(14);
  const [duration, setDuration] = useState(90);
  const [config, setConfig] = useState(null); // eingefrorene Konfiguration des Plans
  const [seeds, setSeeds] = useState(Array(BLOCKS.length).fill(0));

  const plan = useMemo(
    () => (config ? generateTrainingPlan(config.age, config.focus, config.players, config.duration, seeds) : null),
    [config, seeds]
  );

  const generate = () => {
    setConfig({ age, focus, players, duration });
    setSeeds(Array(BLOCKS.length).fill(0));
  };
  const variant = () => setSeeds((s) => s.map((v, i) => v + 1 + i)); // komplette neue Mischung
  const swapBlock = (i) => setSeeds((s) => s.map((v, j) => (j === i ? v + 1 : v)));

  const exportPdf = () => {
    if (!config) return;
    const focusLabel = FOCUS_OPTIONS.find((f) => f.value === config.focus)?.label.replace(/\s+/g, "-");
    const date = new Date().toISOString().slice(0, 10);
    const fileName = `Training_${config.age}_${focusLabel}_${config.players}Spieler_${config.duration}min_${date}`;
    const prevTitle = document.title;
    document.title = fileName; // Browser nutzt den Titel als PDF-Dateinamen
    window.print();
    setTimeout(() => { document.title = prevTitle; }, 1000);
  };

  return (
    <div className="min-h-screen bg-slate-50 font-sans">
      <style>{`
        .print-only { display: none; }
        @media print {
          .screen-only { display: none !important; }
          .print-only { display: block !important; }
          body { background: #fff !important; }
        }
      `}</style>
      <div className="screen-only">
        <Header />
        <main className="mx-auto max-w-2xl space-y-4 px-4 py-4 pb-12">
          <TrainingConfigurator
            age={age} setAge={setAge}
            focus={focus} setFocus={setFocus}
            players={players} setPlayers={setPlayers}
            duration={duration} setDuration={setDuration}
            onGenerate={generate} onVariant={variant}
            hasPlan={!!plan}
          />
          {plan ? (
            <TrainingPlan
              plan={plan}
              players={config.players}
              focus={config.focus}
              age={config.age}
              duration={config.duration}
              onSwapBlock={swapBlock}
              onExportPdf={exportPdf}
            />
          ) : (
            <div className="rounded-2xl border border-dashed border-slate-300 p-8 text-center">
              <p className="text-sm font-medium text-slate-600">
                Jugend, Schwerpunkt, Spieleranzahl und Dauer wählen — dann „Training generieren“ antippen.
              </p>
              <p className="mt-1 text-xs text-slate-400">
                Aufbau nach 7-Block-Struktur, Inhalte angelehnt an die DFB-Trainingsphilosophie
                (kleine Spielformen, hohe Nettospielzeit, Freude · Intensität · Wiederholung).
              </p>
            </div>
          )}
        </main>
      </div>
      {plan && config && <PrintView plan={plan} config={config} duration={config.duration} />}
    </div>
  );
}
