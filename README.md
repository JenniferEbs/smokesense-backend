# SmokeSense Backend

This repository contains the backend for SmokeSense, a digital twin MVP for monitoring indoor air quality during wildfires. The backend simulates outdoor PM₂.₅ levels and calculates indoor room air quality using mock data, enabling a frontend to visualize changes in real time.

## System Overview

- **Cloud Function: `stepPlayback`**  
  - Loads outdoor smoke data from a CSV file  
  - Picks the next outdoor PM₂.₅ value  
  - Recalculates simulated indoor PM₂.₅ for each room using its leak factor  
  - Writes updated values into Firestore  

- **Firestore Database**  
  - `scenarios/outdoorsmoke` → outdoor smoke levels (CSV file)  
  - `rooms/` → leak factors for each room  
  - `sessions/{sessionId}/outdoor/current` → current outdoor PM₂.₅ value  
  - `sessions/{sessionId}/rooms/{roomId}` → simulated indoor PM₂.₅ values per room 

- **Frontend / Mock UI**  
  - Calls `stepPlayback`   
  - Reads Firestore to display outdoor and indoor PM₂.₅ values  
  - Serves as a demo viewer; a full digital twin app could subscribe to Firestore in the same way for real-time overlays  

## Tech Stack

- **Backend / Simulation:** Firebase Cloud Functions (TypeScript)  
- **Database:** Firestore (NoSQL)  
- **Frontend / Mock UI:** HTML + JavaScript (reads Firestore for visualization)  
- **Development Tools:** Node.js, npm, Firebase Emulator Suite

### Demo Video (Database Updates)

[Firestore Database](assets/demo.mp4)
