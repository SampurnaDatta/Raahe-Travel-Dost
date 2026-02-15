# Requirements Document: Raahé 

## Introduction

Raahé is a tourist navigation application optimized for Indian cities that addresses the unique challenges tourists face: complex traffic patterns, diverse transport options, and language barriers. The system provides intelligent, personalized route recommendations by dynamically detecting available transport modes, analyzing real-time conditions, and offering multilingual conversational guidance with live GPS tracking.

## Glossary

- **System**: The Raahé tourist navigation application
- **User**: A tourist or commuter using the application
- **Transport_Mode**: A method of transportation (metro, bus, auto-rickshaw, cab, walking)
- **Route_Option**: A complete journey plan using one or more transport modes
- **User_Preference**: User's priority for route selection (cheapest, fastest, easiest, avoid traffic, balanced)
- **Live_GPS_Mode**: Real-time navigation with GPS tracking and voice alerts
- **Static_Mode**: Text-based step-by-step navigation instructions
- **Regional_Language**: Any of the 20+ Indian languages supported by the system
- **Commute_Mode**: Same as Transport_Mode
- **Route_Deviation**: When user's actual location diverges from planned route
- **Transfer**: A change from one transport mode or vehicle to another during a journey
- **Peak_Hour**: High traffic periods 
- **Walking_Threshold**: Maximum distance (800m) below which walking is always evaluated

## Requirements

### Requirement 1: Dynamic Transport Mode Detection

**User Story:** As a tourist, I want the system to show me only available transport options for my location, so that I don't waste time considering unavailable modes.

#### Acceptance Criteria

1. WHEN the User provides a destination, THE System SHALL detect all available Transport_Modes at the current location
2. WHEN a Transport_Mode is unavailable at the current location, THE System SHALL exclude it from Route_Options
3. WHEN the destination distance is less than Walking_Threshold, THE System SHALL always include walking as a Transport_Mode
4. WHEN the location is in a rural area, THE System SHALL adapt Transport_Mode availability accordingly
5. WHEN the location is in a metro city, THE System SHALL include metro and bus options if available

### Requirement 2: User Preference-Based Route Calculation

**User Story:** As a user, I want to specify my travel priority, so that the system recommends routes matching my needs.

#### Acceptance Criteria

1. THE System SHALL support cheapest route as a User_Preference
2. THE System SHALL support fastest route as a User_Preference
3. THE System SHALL support easiest route as a User_Preference
4. THE System SHALL support avoid traffic as a User_Preference
5. THE System SHALL support balanced option as a User_Preference
6. WHEN a User_Preference is selected, THE System SHALL rank Route_Options according to that preference

### Requirement 3: Comprehensive Route Comparison

**User Story:** As a user, I want to see detailed information about each route option, so that I can make an informed decision.

#### Acceptance Criteria

1. FOR ALL valid Route_Options, THE System SHALL calculate total distance
2. FOR ALL valid Route_Options, THE System SHALL estimate total travel time
3. FOR ALL valid Route_Options, THE System SHALL estimate total cost
4. FOR ALL valid Route_Options, THE System SHALL determine traffic impact level
5. FOR ALL valid Route_Options, THE System SHALL count the number of Transfers
6. FOR ALL valid Route_Options, THE System SHALL calculate total walking distance involved
7. THE System SHALL display all calculated metrics for each Route_Option

### Requirement 4: AI-Powered Route Recommendation

**User Story:** As a user, I want the system to recommend the best route with clear reasoning, so that I understand why it's the optimal choice.

#### Acceptance Criteria

1. WHEN Route_Options are calculated, THE System SHALL rank them based on User_Preference
2. WHEN ranking Route_Options, THE System SHALL adjust for current traffic congestion
3. WHEN presenting the top recommendation, THE System SHALL provide clear reasoning
4. THE System SHALL include estimated arrival time in the recommendation
5. THE System SHALL include estimated cost in the recommendation
6. WHEN traffic conditions change significantly, THE System SHALL update the ranking

### Requirement 5: GPS Location Detection

**User Story:** As a user, I want the system to automatically detect my current location, so that I don't have to manually enter it.

#### Acceptance Criteria

1. WHEN the User initiates a route search, THE System SHALL request GPS permission
2. WHEN GPS permission is granted, THE System SHALL detect the User's current coordinates
3. WHEN GPS permission is denied, THE System SHALL prompt the User to enter location manually
4. THE System SHALL use the detected GPS coordinates as the journey starting point

### Requirement 6: Static Navigation Mode

**User Story:** As a user, I want text-based step-by-step instructions, so that I can follow the route without continuous GPS tracking.

#### Acceptance Criteria

1. WHEN a User selects Static_Mode, THE System SHALL generate complete step-by-step text instructions
2. THE System SHALL include all Transfers in the instructions
3. THE System SHALL include walking directions in the instructions
4. THE System SHALL include estimated time for each step in the instructions
5. THE System SHALL present instructions in the User's selected Regional_Language

### Requirement 7: Live GPS Navigation Mode

**User Story:** As a user, I want real-time GPS tracking with voice alerts, so that I can navigate without constantly checking my phone.

#### Acceptance Criteria

1. WHEN a User selects Live_GPS_Mode, THE System SHALL track the User's GPS coordinates in real-time
2. WHEN the User approaches the next stop or waypoint, THE System SHALL provide a proximity alert
3. WHEN a transport vehicle is arriving soon, THE System SHALL provide a time-based alert
4. WHEN the User is on a multi-stop journey, THE System SHALL provide remaining stops count
5. WHEN Route_Deviation is detected, THE System SHALL alert the User immediately
6. WHEN Route_Deviation occurs, THE System SHALL recalculate the route automatically
7. THE System SHALL provide voice alerts in the User's selected Regional_Language

### Requirement 8: Multilingual Support

**User Story:** As a tourist who may not speak English or Hindi, I want to interact with the app in my native language, so that I can navigate comfortably.

#### Acceptance Criteria

1. THE System SHALL support at least 20 Indian Regional_Languages including English, Hindi, Bengali, Tamil, Telugu, Marathi, Kannada, Malayalam, Gujarati, Punjabi, Odia, and Assamese
2. WHEN a User provides voice input, THE System SHALL detect the Regional_Language automatically
3. WHEN a User selects a Regional_Language, THE System SHALL accept text input in that language
4. WHEN a User selects a Regional_Language, THE System SHALL provide all responses in that language
5. THE System SHALL use locally familiar terminology for Transport_Modes in each Regional_Language
6. WHEN providing navigation instructions, THE System SHALL maintain language consistency throughout the journey

### Requirement 9: Voice Input Processing

**User Story:** As a user, I want to speak my destination in my native language, so that I can use the app hands-free and comfortably.

#### Acceptance Criteria

1. THE System SHALL accept destination input via voice in any supported Regional_Language
2. WHEN voice input is received, THE System SHALL convert it to text accurately
3. WHEN voice input is ambiguous, THE System SHALL ask clarifying questions
4. THE System SHALL confirm the understood destination with the User before proceeding
5. WHEN voice recognition fails, THE System SHALL prompt the User to try again or use text input

### Requirement 10: Conversational AI Interface

**User Story:** As a user, I want to have a natural conversation with the app, so that the experience feels friendly and intuitive.

#### Acceptance Criteria

1. WHEN the User provides incomplete information, THE System SHALL ask clarifying questions
2. THE System SHALL maintain conversational context across multiple interactions
3. WHEN explaining recommendations, THE System SHALL use friendly, conversational tone
4. THE System SHALL adapt responses based on User's language and communication style
5. WHEN the User asks follow-up questions, THE System SHALL provide relevant answers maintaining context

### Requirement 11: Real-Time Traffic Integration

**User Story:** As a user, I want route recommendations that account for current traffic, so that I avoid delays and reach my destination on time.

#### Acceptance Criteria

1. WHEN calculating Route_Options, THE System SHALL incorporate real-time traffic congestion data
2. WHEN current time falls within Peak_Hour, THE System SHALL adjust time estimates accordingly
3. WHEN a festival or event causes crowd spikes, THE System SHALL factor this into recommendations
4. WHEN traffic conditions change during navigation, THE System SHALL update the User proactively
5. THE System SHALL provide traffic impact level for each Route_Option

### Requirement 12: Journey Completion Detection

**User Story:** As a user, I want the system to recognize when I've reached my destination, so that I know my journey is complete.

#### Acceptance Criteria

1. WHEN the User's GPS coordinates match the destination within acceptable tolerance, THE System SHALL detect arrival
2. WHEN arrival is detected, THE System SHALL display a trip successful message
3. WHEN arrival is detected, THE System SHALL stop active navigation
4. THE System SHALL provide journey summary including actual time and distance traveled

### Requirement 13: Route Confirmation Workflow

**User Story:** As a user, I want to review and confirm my chosen route before starting navigation, so that I'm comfortable with the plan.

#### Acceptance Criteria

1. WHEN Route_Options are presented, THE System SHALL wait for User confirmation before starting navigation
2. THE System SHALL allow the User to switch between different Route_Options before confirming
3. WHEN the User confirms a Route_Option, THE System SHALL ask whether to use Static_Mode or Live_GPS_Mode
4. THE System SHALL not start navigation until explicit User confirmation is received

### Requirement 14: Cost Estimation

**User Story:** As a budget-conscious tourist, I want accurate cost estimates for each route, so that I can plan my expenses.

#### Acceptance Criteria

1. FOR ALL Route_Options involving paid Transport_Modes, THE System SHALL estimate the total cost
2. WHEN a Route_Option includes multiple paid Transport_Modes, THE System SHALL sum all costs
3. THE System SHALL display costs in Indian Rupees
4. WHEN cost data is unavailable for a Transport_Mode, THE System SHALL indicate this to the User
5. THE System SHALL update cost estimates based on distance and current pricing

### Requirement 15: Walking Distance Evaluation

**User Story:** As a user, I want to know how much walking is involved in each route, so that I can choose based on my physical capability.

#### Acceptance Criteria

1. FOR ALL Route_Options, THE System SHALL calculate total walking distance
2. WHEN walking distance exceeds 800 meters, THE System SHALL highlight this in the Route_Option display
3. WHEN the destination is within Walking_Threshold, THE System SHALL always present walking as a Route_Option
4. THE System SHALL include walking segments between Transfers in the total walking distance
5. THE System SHALL display walking distance prominently for each Route_Option

### Requirement 16: Transfer Counting and Display

**User Story:** As a user unfamiliar with local transport, I want to know how many times I need to change vehicles, so that I can choose simpler routes.

#### Acceptance Criteria

1. FOR ALL Route_Options, THE System SHALL count the number of Transfers
2. WHEN a Route_Option has zero Transfers, THE System SHALL indicate it as a direct route
3. WHEN User_Preference is set to easiest, THE System SHALL prioritize Route_Options with fewer Transfers
4. THE System SHALL display the Transfer count prominently for each Route_Option
5. THE System SHALL include Transfer locations in the route details

### Requirement 17: Language Detection

**User Story:** As a user, I want the app to automatically detect my language, so that I don't have to manually configure it.

#### Acceptance Criteria

1. WHEN the User first launches the application, THE System SHALL attempt to detect the device language
2. WHEN voice input is provided, THE System SHALL detect the Regional_Language from the audio
3. WHEN automatic detection is uncertain, THE System SHALL ask the User to select their preferred Regional_Language
4. THE System SHALL remember the User's Regional_Language preference for future sessions
5. THE System SHALL allow the User to change Regional_Language at any time

### Requirement 18: Proximity Alert Thresholds

**User Story:** As a user in Live GPS Mode, I want timely alerts before my stop, so that I can prepare to get off without missing it.

#### Acceptance Criteria

1. WHEN the User is within 500 meters of the next stop, THE System SHALL provide a proximity alert
2. WHEN a metro or bus is arriving within 2 minutes, THE System SHALL provide an arrival alert
3. WHEN only 2 stops remain in a multi-stop journey, THE System SHALL alert the User
4. THE System SHALL provide alerts via both visual and voice notifications
5. THE System SHALL not provide alerts more frequently than once per minute for the same waypoint

### Requirement 19: Route Recalculation on Deviation

**User Story:** As a user who might take a wrong turn or miss a stop, I want the system to automatically fix my route, so that I can still reach my destination.

#### Acceptance Criteria

1. WHEN Route_Deviation exceeds 100 meters from the planned path, THE System SHALL detect it
2. WHEN Route_Deviation is detected, THE System SHALL recalculate the route from the current location
3. WHEN recalculating, THE System SHALL maintain the original User_Preference
4. THE System SHALL notify the User that the route has been updated
5. WHEN recalculation is not possible, THE System SHALL prompt the User to select a new route

### Requirement 20: Balanced Route Option

**User Story:** As a user who wants a reasonable compromise, I want a balanced route that considers multiple factors, so that I get a well-rounded option.

#### Acceptance Criteria

1. WHEN User_Preference is set to balanced, THE System SHALL consider cost, time, and ease equally
2. WHEN calculating balanced ranking, THE System SHALL normalize all metrics to comparable scales
3. WHEN multiple Route_Options have similar balanced scores, THE System SHALL present all of them
4. THE System SHALL explain what factors contributed to the balanced recommendation
5. THE System SHALL not favor any single metric disproportionately in balanced mode

