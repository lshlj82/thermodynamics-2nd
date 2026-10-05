# Entropy and the Second Law of Thermodynamics

This is an interactive, browser-based demo of the second part of thermodynamics. It covers irreversibility and the arrow of time, entropy as a state function, the second law, heat engines and the Carnot cycle, efficiency, refrigerators, why no engine beats a Carnot engine, and the statistical meaning of entropy. It comes as two separate pages, one in English and one in Korean.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee (이상훈)**.

> **한국어 요약:** 시간의 흐름과 비가역성, 엔트로피 변화, 열역학 제2법칙, 열기관과 Carnot 순환, 열효율과 T–S 그림, 냉동기, Carnot 기관보다 효율이 좋은 기관이 없는 이유, 통계역학적 관점의 엔트로피와 Boltzmann 엔트로피 S = k ln W를 직접 조작해 볼 수 있는 인터랙티브 웹 데모입니다. 이상훈(Sang Hoon Lee)의 강의 노트를 바탕으로 Claude Opus 5.5가 만들었습니다. 한국어 페이지는 `thermo2-ko.html`입니다.

## Files

| File | Description |
| --- | --- |
| `thermo2-en.html` | American English version |
| `thermo2-ko.html` | Korean version (한국어) |
| `README-thermo2.md` | This file |

Each page is a single self-contained HTML file with inline CSS and JavaScript. There is no build step and there are no dependencies. The only external request is to Google Fonts for IBM Plex Sans KR. If that request fails, the page falls back to system fonts. Each page links to the other language from its top bar. Equations use real fraction bars, radical signs, and stacked sub- and superscripts, and halves are written as (1/2).

## Running it

Open either file directly in a modern browser, or serve the folder locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/thermo2-en.html
```

### Publishing on GitHub Pages

1. Push these files to a repository.
2. In **Settings → Pages**, choose **Deploy from a branch**, then select your branch and the root folder.
3. Visit `https://<user>.github.io/<repo>/thermo2-en.html` or `.../thermo2-ko.html`.

These pages can share a repository with the other demos in the series (`motion-*`, `newton-*`, `energy-*`, `momentum-*`, `rotation-*`, `oscillation-wave-*`, `thermo1-*`, `gauss-*`, `circuits-*`, `rc-*`, `magnetism-*`, `induction-*`, `maxwell-*`). The file names don't collide. The first part of thermodynamics, on temperature, heat and the first law, is `thermo1-*`.

## What's inside

The nine sections follow the order of the lecture notes. Every value is recomputed live as you move the controls.

1. **Irreversibility:** Molecules start in the left half of an insulated box, and the stopcock opens. A graph follows the fraction on the left as it settles near 1/2. The page gives $\ln W$ of the current configuration, the chance $2^{-N}$ that all molecules are back on the left, and $R\ln 2$ for one mole doubling its volume.
2. **Change in entropy:** One mole of a monatomic gas goes between the same two states along two reversible paths (isothermal then isochoric, or isochoric then isothermal). The simulation adds up $\int dQ/T$ along each path, and both agree with $\Delta S = nR\ln(V_f/V_i)+nC_V\ln(T_f/T_i)$.
3. **The second law:** Reversible isothermal compression or expansion on a reservoir, with lead shot on the piston, or a free expansion. Bars show $\Delta S_\text{gas}$, $\Delta S_\text{res}$ and the total: 0 for the reversible processes, positive for the free expansion.
4. **The Carnot cycle:** The four stages (isothermal expansion at $T_H$, adiabatic expansion, isothermal compression at $T_L$, adiabatic compression) on a $p$–$V$ diagram. A cylinder sits on the hot reservoir, the cold reservoir or insulation. The page gives $|Q_H|$, $|Q_L|$, $W$, and checks that $|Q_H|/T_H=|Q_L|/T_L$.
5. **Efficiency and real engines:** The Carnot cycle drawn as a rectangle on a $T$–$S$ diagram, next to an engine whose efficiency you set. Arrow widths show $|Q_H|$, $W$ and $|Q_L|$. The page compares your efficiency with $\varepsilon_C = 1-T_L/T_H$ and reports whether the second law allows it, makes it reversible, or rules it out. An efficiency of 100% is a perfect engine.
6. **Refrigerators:** A refrigerator removes heat from a cold room and releases it outside. You set its coefficient of performance $K$ and compare it with $K_C = T_L/(T_H-T_L)$, plotted against the temperature difference. A switch turns it into a perfect refrigerator, which violates the second law.
7. **Nothing beats Carnot:** An engine X drives a Carnot refrigerator between the same reservoirs, as in the notes' proof. If X is more efficient than a Carnot engine, the combined device becomes a perfect refrigerator, moving heat from cold to hot with no work.
8. **Microstates:** $N$ numbered molecules (2 to 12) hop at random between the two halves of a box. Bars show the multiplicity $W = N!/(n_1!\,n_2!)$, the current configuration is highlighted, and dots show how often each configuration has occurred. The page gives $W$, $S = k\ln W$, the probability $W/2^N$, and the total number of microstates.
9. **Boltzmann entropy:** For $N$ from 10 to $10^{24}$, the page plots $W/W_\text{max}$ against the percentage of molecules on the left and shows the central peak narrowing. It gives the width of the peak, the chance of finding at least 51% on the left, and $S = k\ln W$ of the central configuration. $Nk\ln 2$ equals $nR\ln 2$, the thermodynamic $\Delta S$ of a free expansion to twice the volume.

The header animation shows a free expansion. A gas spreads through an opening in a partition, while a graph shows the entropy rising and leveling off, labeled $\Delta S > 0$.

## Notes on the model

- **Working substance:** The Carnot cycle and the entropy calculations use one mole of a monatomic ideal gas ($C_V = \tfrac32 R$, $\gamma = 5/3$).
- **Fixed amounts per cycle:** The engine takes $|Q_H| = 1000$ J per cycle, the refrigerator removes $|Q_L| = 1000$ J per cycle, and engine X delivers $W = 500$ J per cycle.
- **Numerical check:** In section 2, $\int dQ/T$ is added up numerically along each path, so the agreement with the formula is a real check, not the formula shown twice.
- **Large-N approximation:** For large $N$, section 9 uses Stirling's approximation. The peak is drawn as a Gaussian, and very small probabilities are shown as powers of ten.
- **Hopping model:** In section 8 one molecule chosen at random switches sides at each step, so in the long run every microstate is equally likely, which is the basic assumption of statistical mechanics.
- **Display:** The pages follow the system's light or dark setting. Under `prefers-reduced-motion`, the animations start paused and can be played by hand. Only simulations that are currently on screen are animated.

## Credits

- Lecture notes: Sang Hoon Lee (이상훈)
- Demo design and code: Claude Opus 5.5

## License

No license has been chosen yet. Before publishing, add a `LICENSE` file if you want others to be able to reuse the code. Also confirm with the author of the lecture notes how their material may be shared.
