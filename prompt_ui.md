  I have a working PyQt5 lab DAQ GUI (experiment.py or similar — find the main file). I want to improve the visual design without changing any functionality. Here is what to do:   
                                                                                                                                                                                    
  1. Apply a dark Fusion theme globally
  At app startup, set app.setStyle('Fusion') and apply a dark QPalette. Background #1a1a1a, slightly lighter panels #222222, border/mid color #3a3a3a, bright text #e2e2e2, dimmed  
  text #888888, highlight color #4f9cf9.                                                                                                                                            
   
  2. Load IBM Plex fonts                                                                                                                                                            
  Download IBMPlexSans-Regular.ttf, IBMPlexSans-Medium.ttf, IBMPlexMono-Regular.ttf from Google Fonts and place them in a fonts/ subfolder. Load them at startup with
  QFontDatabase.addApplicationFont(). Use IBM Plex Sans for all UI labels and buttons, IBM Plex Mono for all numeric readout values.                                                
   
  3. Restyle the reading cards                                                                                                                                                      
  Each card (P1, P2, dP, T) should have a dark background (#1e1e1e), no border-radius, a 2px solid colored top border (keep the existing channel colors), and the numeric value
  rendered in IBM Plex Mono at a large size. Remove the colored background fill — dark background only.                                                                             
                                                            
  4. Style the pyqtgraph plots                                                                                                                                                      
  - Set plot background to #141414                          
  - Set axis/tick label color to #555555                                                                                                                                            
  - Set grid lines with showGrid(x=True, y=True, alpha=0.06)
  - For each curve, add fillLevel=0 and a semi-transparent brush matching the line color at ~25 alpha (0–255 scale) for the fill under the curve                                    
  - Keep all existing curve colors                                                                                                                                                  
                                                                                                                                                                                    
  5. Style the controls section                                                                                                                                                     
  - Dark background matching the main window                                                                                                                                        
  - Buttons: flat style, #2a2a2a background, #3a3a3a border, #e2e2e2 text, no border-radius. Hover state: slightly lighter background.                                              
  - Start Logging button: #4f9cf9 background, white text, same flat style                                                             
  - Input fields: #111111 background, #3a3a3a border, #4f9cf9 text color (monospace font)                                                                                           
  - Section label "Controls" in small uppercase IBM Plex Sans, #555 color                
                                                                                                                                                                                    
  6. Status bar                                                                                                                                                                     
  The existing "Simulation mode — no DAQ detected" strip at the bottom: dark background #1a1a1a, left border 3px solid #f87171 (red) for simulation/error states, 3px solid #4ade80 
  (green) for connected. IBM Plex Sans, small text.                                                                                                                                 
                                                            
  Do not change any acquisition logic, signal connections, data structures, or layout geometry. Only change visual styling. 
