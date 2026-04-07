# TravelBuddy — Trợ lý Du lịch Thông minh

AI Agent tư vấn du lịch Việt Nam sử dụng LangGraph + OpenRouter.

## Stack
- **LangGraph** — Agent loop (StateGraph)
- **LangChain** — Tool binding, message handling
- **OpenRouter** — LLM API (Qwen)
- **Python 3.12**

## Cấu trúc
```
lab4_agent/
├── agent.py          # LangGraph graph + chat loop
├── tools.py          # 3 custom tools: flights, hotels, budget
├── system_prompt.txt # Persona + rules + tool instructions
├── test_results.md   # Kết quả 9 test cases
├── .env              # API key
└── README.md
```

## Setup

```bash
python -m venv venv
source venv/bin/activate
pip install langchain langchain-openai langgraph python-dotenv
```

Tạo file `.env`:
```
OPENROUTER_API_KEY=sk-or-v1-...
```

## Chạy

```bash
python agent.py
```

## Tools

| Tool | Mô tả |
|------|-------|
| `search_flights` | Tìm chuyến bay giữa 2 thành phố |
| `search_hotels` | Tìm khách sạn theo thành phố + ngân sách |
| `calculate_budget` | Tính tổng chi phí và tiền còn lại |

## Test Results

9/9 test cases PASS — xem chi tiết trong `test_results.md`.