# Microservice_Fastapi_flask
building microservice with fastapi and flask <br>
---
![fastapi](https://github.com/user-attachments/assets/7604f4c3-032f-440a-9d8d-e8784d12fd5b)
<img width="359" height="140" alt="flask" src="https://github.com/user-attachments/assets/8c26a23f-6273-4373-b378-3b9236fed928" />
<img width="259" height="194" alt="microservice" src="https://github.com/user-attachments/assets/0e2107d7-cee0-45b7-83ff-8ffb0e915826" />
<img width="227" height="222" alt="kubernetes" src="https://github.com/user-attachments/assets/324738f4-7fd2-4428-9006-54d1b5bbfc96" />
---
# Microservices vs Monolith: A Detailed Comparison

## **What are Microservices?**
Microservices is an architectural style that structures an application as a collection of loosely coupled services. Each service:
- Is independently deployable
- Focuses on a specific business capability
- Has its own data storage when needed
- Communicates via lightweight APIs (typically HTTP/REST or messaging)

**Example:** An e-commerce application might have separate microservices for:
- User management
- Product catalog
- Order processing
- Payment processing
- Recommendation engine

## **What is a Monolith?**
A monolithic architecture is a traditional unified model where all application components are tightly integrated into a single program, sharing:
- A single codebase
- A single database
- A single deployment unit
- The same runtime environment

**Example:** The same e-commerce application built as one cohesive unit where all functions run together.

## **Pros and Cons: Microservices vs Monolith**

### **Microservices Advantages:**
1. **Independent Development** - Teams can work on different services simultaneously
2. **Independent Deployment** - Update one service without redeploying the whole application
3. **Technology Diversity** - Use different technologies/frameworks per service
4. **Scalability** - Scale only the services that need it
5. **Fault Isolation** - Failure in one service doesn't necessarily bring down the whole system
6. **Easier to Understand** - Each service has a focused scope

### **Microservices Disadvantages:**
1. **Complexity** - Distributed system complexities (network latency, fault tolerance)
2. **Data Consistency** - Maintaining transactions across services is challenging
3. **Operational Overhead** - Requires containerization, orchestration (Kubernetes), monitoring
4. **Network Complexity** - Service-to-service communication adds latency
5. **Testing Challenges** - End-to-end testing requires all dependent services
6. **Higher Initial Cost** - More infrastructure and DevOps investment

### **Monolith Advantages:**
1. **Simpler Development** - Single codebase, easier to get started
2. **Easier Debugging** - All code runs in one process
3. **Consistent Data** - ACID transactions are straightforward
4. **Less Infrastructure** - No need for service discovery, API gateways, etc.
5. **Simpler Deployment** - Deploy one package/executable
6. **Performance** - In-process calls are faster than network calls

### **Monolith Disadvantages:**
1. **Slower Development** - Large codebase becomes hard to manage
2. **Scalability Challenges** - Must scale the entire application
3. **Technology Lock-in** - Difficult to adopt new technologies
4. **Single Point of Failure** - Bug can crash the entire application
5. **Rigid Structure** - Difficult to change or refactor large codebase
6. **Slower Deployment** - Small changes require full application redeployment

## **When to Choose Which?**

### **Start with Monolith If:**
- You're building an MVP or starting a new project
- Your team is small
- Application complexity is low
- You need to move quickly to market
- You don't have DevOps expertise

### **Consider Microservices If:**
- You have multiple teams working on the same product
- Different parts of your system have different scalability needs
- You need to use different technologies for different functionalities
- You have DevOps expertise and infrastructure
- Your monolith has become too complex to manage

## **Best Practices:**
- **Don't start with microservices** unless you have a clear need
- Consider the **"Monolith First"** approach (build, then break apart when needed)
- If using microservices, implement proper **observability** (logging, monitoring, tracing)
- Design services around **business capabilities**, not technical layers
- Implement **circuit breakers** and **retry mechanisms** for inter-service communication

## **Hybrid Approach:**
Many organizations successfully use a hybrid model where:
- Core business logic remains in a monolith
- Specific functionalities are extracted as microservices when needed
- This allows gradual migration without complete rewrite

The choice depends on your team size, expertise, application requirements, and organizational structure. There's no one-size-fits-all solution—both architectures have their place in modern software development.

## Prepare enviroments: <br>
```bash
# sudo apt install python3 python3-pip python3-virtualenv
```
create virtual environments <br>
```bash
# virtualenv env
# source env/bin/activate
```
install fastapi : <br>
```bash
# pip3 install fastapifastapi[standard]
```
create main.py file : <br>
```bash
# vi main.py
```
create simple app like this : <br>
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")

async def root():
    return {"message": "Hello World"}
```
and then you can start your app with below command : <br>
```bash
fastapi dev main.py --host 0.0.0.0 --port 8000
```
![1](https://github.com/user-attachments/assets/6ef85b8c-3cc0-46e6-a7b5-2664a81a9740) <br>
![2](https://github.com/user-attachments/assets/1768ac80-9066-4e66-9b74-fd26202cb2b8) <br>

or we can use uvicorn to expose port and use python to run program : <br>
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")

async def root():
    return {"message": "Hello World"}

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)

```
![3](https://github.com/user-attachments/assets/196ef443-e8bc-4c7f-aafa-c9313af6f0b6) <br>


