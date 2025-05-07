
# Text Processing Commands Guide

1. [AWK Command](#1-awk-command)
2. [SED Command](#2-sed-command)
3. [GREP Command](#3-grep-command)

## SAMPLE LOG FILE FOR EXAMPLES
```
03/22 08:52:51 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Exiting
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: RSVPPutActionName:  Result = 0
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: RSVPPutActionName:  Exiting
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: flow[sess=9.67.116.99:1047:6, 
source=9.67.116.98:8000] registered with CLCat2
03/22 08:52:52 EVENT  :..........qosmgr_response: RESVRESP from qosmgr, reason=0, qoshandle=8b671d0
03/22 08:52:52 INFO   :..........qosmgr_response: src-9.67.116.98:8000 dst-9.67.116.99:1047 proto-6
03/22 08:52:52 TRACE  :...........traffic_reader: tc response msg=1, status=1
03/22 08:52:52 INFO   :...........traffic_reader: Reservation req successful[session=9.67.116.99:1047:6,
source=9.67.116.98:8000, qoshd=8b671d0]
 20 
03/22 08:52:52 TRACE  :........api_action_sender: constructing a RESV
03/22 08:52:52 TRACE  :........flow_timer_stop: stopped T1
03/22 08:52:52 TRACE  :........flow_timer_stop: Stop T4
03/22 08:52:52 TRACE  :........flow_timer_start: started T1

```

## 1. AWK Command
AWK is used for pattern scanning and text processing.

### Basic Syntax
```bash
awk 'pattern {action}' filename
```

### Common Examples

1. **Print entire file**
```bash
awk '{print}' sample.log
Output:
03/22 08:52:51 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Exiting
```

2. **Print specific columns**
```bash
awk '{print $1,$2}' sample.log   # Print first and second columns
Output:
03/22 08:52:51
03/22 08:52:52
```

3. **Pattern matching with count**
```bash
awk '/INFO/{count++} END {print "Total INFO messages: " count}' sample.log
Output:
Total INFO messages: 12
```

4. **Time range filtering**
```bash
awk '$2 >= "08:53:00" && $2 <= "08:53:59" {print $2, $3, $4}' sample.log
Output:
08:53:07 EVENT :..mailslot_sitter:
08:53:22 TRACE :.....rsvp_event:
```

5. **Print with line numbers**
```bash
awk 'NR >=1 && NR <=3 {print NR, $2, $3, $4}' sample.log
Output:
1 08:52:51 INFO :..........rpapi_Reg_UnregFlow:
2 08:52:52 INFO :..........rpapi_Reg_UnregFlow:
3 08:52:52 INFO :..........rpapi_Reg_UnregFlow:
```

## 2. SED Command
SED is a stream editor for filtering and transforming text.

### Basic Syntax
```bash
sed [options] 'command' filename
```

### Common Examples

1. **Print lines matching pattern**
```bash
sed -n '/INFO/p' sample.log
Output:
03/22 08:52:51 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Exiting
```

2. **Substitute text**
```bash
sed 's/INFO/LOG/p' sample.log
Output:
03/22 08:52:51 LOG   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
03/22 08:52:52 LOG   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Exiting
```

3. **Line number with pattern**
```bash
sed -n -e '/TRACE/=' -e '/INFO/p' sample.log
Output:
8
03/22 08:52:51 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
11
```

## 3. GREP Command
GREP is used for searching text patterns in files.

### Basic Syntax
```bash
grep [options] pattern filename
```

### Common Examples

1. **Case-insensitive search**
```bash
grep -i 'info' sample.log
Output:
03/22 08:52:51 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Entering
03/22 08:52:52 INFO   :..........rpapi_Reg_UnregFlow: ReadBuffer:  Exiting
```

2. **Show line numbers**
```bash
grep -n 'TRACE' sample.log
Output:
8:03/22 08:52:52 TRACE  :...........traffic_reader: tc response msg=1, status=1
11:03/22 08:52:52 TRACE  :........api_action_sender: constructing a RESV
```

3. **Count matches**
```bash
grep -c 'INFO' sample.log
Output:
12
```

## Advanced Usage: Combining Commands

1. **Process listing with filtering**
```bash
ps aux | grep ubuntu | awk '{print $1,$2}'
Output:
ubuntu 1234
ubuntu 5678
```

2. **Log analysis pipeline**
```bash
grep 'INFO' sample.log | awk '{print $1,$2,$4}' | sed 's/INFO/LOG/'
Output:
03/22 08:52:51 LOG :..........rpapi_Reg_UnregFlow:
03/22 08:52:52 LOG :..........rpapi_Reg_UnregFlow:
```
