# CampusMarket API Specification

Base URL: `http://localhost:3000/api/v1`

All responses are JSON. Login uses a token that expires in 1 hour.
Protected endpoints need this header: `Authorization: Bearer <token>`

## Endpoints

| Method | Path | Needs token | Request body | Success | Errors |
|---|---|---|---|---|---|
| GET | `/health` | No | none | 200 `{"status":"ok"}` | none |
| POST | `/sessions` | No | `{"email","password"}` | 200 `{"token","user":{"id","name","email"}}` | 400 `{"error":"Email and password are required."}`, 401 `{"error":"Invalid email or password."}` |
| GET | `/users/me` | Yes | none | 200 `{"id","name","email"}` | 401 `{"error":"Not logged in."}` |

## Other responses

| Case | Status | Body |
|---|---|---|
| Unknown route | 404 | `{"error":"Not found."}` |
| Server crash | 500 | `{"error":"Something went wrong."}` |

The same 401 message is used for an unknown email and a wrong password, so nobody can guess which emails exist. The password and its hash are never sent. Stack traces are never sent.

## Listings (design only)

These endpoints are a plan. They are not built yet.

| Action | Method | Path | Needs token | Success | Errors |
|---|---|---|---|---|---|
| List all listings | GET | `/listings` | No | 200 list of listings | none |
| Filter by category | GET | `/listings?category=books` | No | 200 list of listings in that category | 400 if category is not books, gadgets, clothes, or food |
| Get one listing | GET | `/listings/:id` | No | 200 one listing | 404 `{"error":"Not found."}` |
| Add a listing | POST | `/listings` | Yes | 201 the new listing | 400 missing fields, 401 not logged in |
| Change a listing | PATCH | `/listings/:id` | Yes (owner only) | 200 the updated listing | 400, 401, 403, 404 |
| Delete a listing | DELETE | `/listings/:id` | Yes (owner only) | 204 no body | 401, 403, 404 |

Example listing: `{"id":1,"title":"Calculus textbook","price":350,"category":"books","sellerId":4}`