# Incident Report: Ipubers Database CPU Spike
**Date:** May 22, 2026  
**Time:** 09:50 AM  
**Duration:** [To be determined - ongoing/resolved]  
**Severity:** High  
**Status:** Resolved/Ongoing

---

## Executive Summary

An incident occurred at 09:50 AM on May 22, 2026, where the Ipubers database experienced a critical CPU spike reaching nearly 100% utilization. This caused service degradation for dependent APIs, specifically impacting the API Integrasi Kartan service while the API Core Ipubers remained unaffected.

---

## Incident Timeline

| Time | Event |
|------|-------|
| 09:50 AM | CPU spike detected - DB CPU utilization reached ~100% |
| [Time] | First service impact observed (API Integrasi Kartan) |
| [Time] | Incident investigation initiated |
| [Time] | Root cause identified |
| [Time] | Mitigation applied / Incident resolved |

---

## Impact Analysis

### Affected Services
- **API Integrasi Kartan**: ✅ **IMPACTED**
  - Error rate increased due to cancellation tokens
  - Service experienced degradation

- **API Core Ipubers**: ✅ **NOT IMPACTED**
  - Continued normal operations
  - No error rate increase observed

### Metrics
- **Database CPU Utilization**: ~100% (spike during incident)
- **Baseline CPU Utilization**: Normal at 2 hours prior
- **Active Connections**: Significant increase during incident period (see connection analysis below)

---

## Root Cause Analysis

### Primary Observation: Database Blocking

The incident was characterized by significant database query blocking:

1. **Blocking Overview (Blocking State)**
   - Multiple queries held locks preventing other operations
   - Cascading effect on dependent services

2. **Blocking Overview (Waiting State)**
   - High number of queries waiting for locks to be released
   - Queue buildup leading to connection exhaustion

3. **Blocking Samples**
   - Specific query analysis identified problematic operations
   - Lock contention on critical tables

### Connection Analysis

- **Active Connections During Incident**: Significantly elevated compared to normal baseline
- **Comparison with Normal Operations**: 2 hours prior showed substantially lower connection count
- **Pattern**: Spike correlated with CPU utilization increase

---

## Contributing Factors

1. **Query Lock Contention**: Multiple long-running queries holding exclusive locks
2. **Connection Pool Saturation**: Active connections exceeded normal baseline
3. **Cascading Failures**: Cancellation tokens triggered in API Integrasi Kartan
4. **Service Dependency**: API Integrasi Kartan dependent on Ipubers DB for operations

---

## Resolution

- [Details of resolution steps to be added]
- [Mitigation actions taken]
- [Services returned to normal operation]

---

## Recommendations

### Immediate Actions
1. Review and optimize long-running queries causing lock contention
2. Implement query timeout mechanisms to prevent indefinite blocking
3. Monitor active connection counts for early warning signs

### Short-term Actions
1. Analyze blocking patterns and identify problem queries
2. Consider connection pooling optimization
3. Implement circuit breaker pattern in API Integrasi Kartan for resilience

### Long-term Actions
1. Database performance tuning and indexing review
2. Architecture assessment for database dependency patterns
3. Implement comprehensive database monitoring and alerting
4. Load testing to establish acceptable connection limits
5. Documentation of incident response procedures

---

## Lessons Learned

- [To be documented post-incident]

---

## Attachments

- Database CPU utilization graph (incident period)
- Blocking overview metrics
- Connection analysis charts
- Service error rate comparisons

---

**Prepared by:** [Your Name]  
**Report Date:** May 22, 2026  
**Next Review:** [Date]
