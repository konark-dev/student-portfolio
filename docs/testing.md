# Testing

## 1. Testing Strategy

Test the system incrementally and end-to-end. Core P0 functionality must
be stable before adding P1/P2 features.

## 2. Test Levels

### Unit Tests

Test: - Calculations - Validation - Utility functions - AI tool logic

### Integration Tests

Test: - API + database - Authentication + authorization - AI tools +
backend - Frontend + API

### End-to-End Tests

Test complete user journeys.

## 3. Core Test Cases

  -----------------------------------------------------------------------
  ID                Scenario          Expected Result   Status
  ----------------- ----------------- ----------------- -----------------
  T-001             User logs in      Correct dashboard ⬜
                                      shown             

  T-002             User opens        Correct profile   ⬜
                    profile           data shown        

  T-003             User views        Correct           ⬜
                    attendance        attendance shown  

  T-004             User asks AI      AI uses           ⬜
                    about attendance  authoritative     
                                      attendance data   

  T-005             User asks for     Deterministic     ⬜
                    attendance        calculation is    
                    calculation       correct           

  T-006             Unauthorized user Request rejected  ⬜
                    requests another                    
                    user's data                         

  T-007             AI cannot         AI clearly states ⬜
                    retrieve          data unavailable  
                    unavailable data                    
  -----------------------------------------------------------------------

## 4. AI Evaluation

For each important AI capability test:

-   Correct tool selected?
-   Correct data retrieved?
-   No fabricated values?
-   Correct calculation?
-   Safe response?
-   Useful explanation?

## 5. Performance

Measure where relevant: - API latency - AI response latency - Database
query latency - Error rate - Concurrent users

## 6. Security Testing

-   Authentication bypass
-   Authorization bypass
-   Input validation
-   API abuse
-   Prompt injection attempts
-   Unauthorized AI tool use
-   Sensitive-data exposure

## 7. Demo Test

Before the SIH presentation, run the complete demo from a clean
environment and verify every P0 feature.
