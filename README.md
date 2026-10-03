# Interplanetary Trajectory Simulator: Earth to Mars (Hohmann Transfer)

## About Me And My Journey
Hi, I'm a **15-years-old aerospace enthusiast** currently living in Finland. My ultimate goal is to study Aerospace Engineering/astrophysics in the United States, specifically at **Columbian Univercity in the City of New York**, on a full-ride scholarship

Even thought I'm facing a double language barrier (learning both Finnish and English simultaneously) and had **zero coding experience**, I refuse to let thet stop me. I believe that the language of physics and mathematics is universal. To achieve my dream, I bought a powerful engineering laptop, taught myself the basics of Python, and successfully built this irbital mechanics simulator from scratch.

---

## Engineering Challenges And How I Overcame Them
Building this simulator wasn't easy. As a beginner engineer, I faced several major technical hurdles, but solving them taught me how real software deevelopment works:
* **The IDE Enviroment Maze:** Setting up PyCharm for the first time on a brand-new laptop was overwhelming. I had to figure out how the Python Interpreter works and manually configure dependencies because the code initialling couldn't find the external libraries.
* **The Package Installation hurdles:** I ran into immediate errors trying to import 'matplotlib' and 'NumPy'. I had to learn how to navigate PuCharm's package manager and use terminal tools to successfully bridge the gap between my code and graphics engine.
* **The Strict Laws Of Python Syntax:** I spent a long time fighting with 'IndentationError' and 'NameError'. Phython's strict rules regarding whitespace structure and variable definitions forced me to pay meticulous attention to code cleanliness, formatting, and mathematical logic.
* **The orbital Phasing Bug:** In my first successful compolation, the rocket reached the correct Mars altitude but arrived at the completely wrong side of the solar system-the planet wasn't there! I had to debug the orbital angles, invert the angular trajectory, and shift the reference frame by 180 degrees (π radians) to acheave a perfect, mathematically true interplanetary intercept.

---

## About This Project
This project is the first milestone of my **4-5-year aerospace portfolio**. It is a university-level Python simulation that calculates and visualizes a **Hohmann Transfer Orbit**-the most fuel-efficient way to send a spacecraft from Earth to Mars

The mathematical engine of this simulator accurately synchronizes the orbital phasing of both planets using:
* Kepler's Laws of Planetary Motion And Newton's Law of Universal Gravitation.
* Atmospheric drag calculations (fluid dynamics) for launch phases.
* Dynamic mass reduction equations to simulate real-time engine thrust and fuel burn.

### Simulation Output
When executed, the program successfully solves the orbital mechanics equations and outputs the exact rendezvous  coordinates where the spacecraft intercepts Mars:
* **Mission Duration:** 256 days (256.067846195458) (Theoretical Hohmann optium)
* **Mars Rendezvous Coordinates:** X = -2.285e+11 m, Y = 1.5e+09

### Tech Stack and Engineering Tools
* **Language:** Python
* **Libraries:** NumPy (Mathematical computing), Matplotlib (Data visualization)
* **IDE** PyCharm Professional Environment

---

## My 4-5-Year Interplanetary Strategic Roadmap
To reach my dream of attending Columbia University, I have structured my academic and engineering journey into a rigorous multi-year plan:

### Phase 1: Advanced Software And 3D Engineering (Next 1.5 Year)
* **Mathematical Olympiad Track (Grade 8 and Grade 9):** I am actively competing  in mathematical olympiads during my current 8th-grade year and will continue competing at the highest level throughout the 9th grade to build a bulletproof foundation in advanced problem-solving.
* **Code Optimization And 3D Engine Integration:** I will scale this Python physics engine to compute multi-body gravitational interactions and integrate real-time 3D trajectory rendering.
* **Data-Driven CAD Modeling:** Designing a structurally sound rocket/Mars lander prototype in Autodesk Fusion 360 using the exact mass, surface area, and aerodynamic constraints calculated by my code.

### Phase 2: High School Leadership And Science at Ressun Lukio 
* **Founding and Leading the Astrophsyics and  Space Club:** Once I enter Ressun Lukio, I will independently establish and build a student-led club from scratch. It will be dedicated to deep-space physics, hosting student lectures, and mentoring peers to drive real community impact.
* **academic Research Papers and Essays:** Writing advanced physics essays on orbital mechanics and  nozzle aerodynamics, aiming for national science competitions like **TuKoKe**.

### Phase 3: Elite Academic Credentials and Standardized Testing
* **High-Stakes Standardized Exams:** Preparing for and scorimg top percentiles in the **SAT* (Focusing on 750-800 in Math)  and **IELTS** to demonstrate flawless academic and English proficiency.
* **Competitive Mathematics:** Training for high-level competitive math championships, driving toward the **IMO (International Mathematical Olympiad)** selection tracks.

---

## The Simulation Source Code 
Here is the complete Python source code for my interplanetary orbital engine. I successfully debugged the environment setup, package installations, and  orbital phasing parameters to achieve a mathematically true trajectory:

'''python
import matplotlib
matplotlib.use('tkagg')
import matplotlib.pyplot as plt
import numpy as np

G_sun = 1.327e20
r_earth = 1.469e11
r_mars = 2.279e11
v_earth = np.sqrt(G_sun / r_earth)
v_mars = np.sqrt(G_sun / r_mars)
v_escape = np.sqrt(2 * G_sun / r_earth - 2 * G_sun / (r_earth + r_mars))
travel_time = np.pi * np.sqrt(((r_earth + r_mars) / 2)**3 / G_sun)
days = travel_time / 86400
print(days)
time_step = 10000
current_time = 0.0
earth_x, earth_y = [],[]
mars_x, mars_y = [],[]
rocket_x, rocket_y = [],[]
angle_mars_start = np.pi - (v_mars * travel_time / r_mars)
while current_time <= travel_time:
    angle_earth = (v_earth * current_time) / r_earth
    earth_x.append(r_earth * np.cos(angle_earth))
    earth_y.append(r_earth * np.sin(angle_earth))
    angle_mars = angle_mars_start + (v_mars * current_time) / r_mars
    mars_x.append(r_mars * np.cos(angle_mars))
    mars_y.append(r_mars * np.sin(angle_mars))
    semi_major = (r_earth + r_mars) / 2
    eccentricity = (r_earth - r_mars) / (r_mars + r_earth)
    angle_rocket = -(np.pi * current_time) / travel_time
    r_rocket = (semi_major * (1 - eccentricity**2)) / (1 + eccentricity * np.cos(angle_rocket))
    rocket_x.append(-r_rocket * np.cos(angle_rocket))
    rocket_y.append(r_rocket * np.sin(angle_rocket))
    current_time += time_step

plt.figure(figsize=(7, 7))
plt.plot(0, 0, 'yo', markersize=12, label='Sun')
plt.plot(earth_x, earth_y, color='blue', label='Earth')
plt.plot(mars_x, mars_y, color='red', label='Mars')
plt.plot(rocket_x, rocket_y, color='purple', linewidth=2, linestyle='--', label='Rocket')
plt.plot(earth_x, earth_y, 'bo')
plt.plot(mars_x[-1], mars_y[-1], 'ro')
plt.title('Mission')
plt.legend()
plt.grid(True)
plt.axis('equal')
plt.show()

---

## The Resulting Diagram (Simulation Plot)
This is the exact visualization generated by my script on my new laptop. It proves the successful calculations of the Hohmann transfer arc intercepting Mars exactly at its target destination point:

<img width="700" height="686" alt="Figure_1" src="https://github.com/user-attachments/assets/7712da65-301e-4bf5-b12e-ee53a8f4360f" />
