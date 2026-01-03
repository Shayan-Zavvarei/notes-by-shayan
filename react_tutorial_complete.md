# Complete React Development Tutorial: Beginner to Advanced

## Introduction

React is a JavaScript library for building user interfaces, created and maintained by Meta (Facebook). It enables developers to create interactive, dynamic web applications using a component-based architecture. This tutorial will guide you from fundamental concepts to advanced techniques, providing hands-on examples and practical projects along the way.

## Prerequisites

Before starting, you should have:
- Basic knowledge of HTML, CSS, and JavaScript (ES6+)
- Node.js and npm installed on your system
- A code editor (VS Code recommended)
- Understanding of JavaScript concepts: arrow functions, destructuring, array methods, promises

## Getting Started with React

### Setting Up Your Development Environment

To create a new React application, use Vite, a modern build tool that provides faster development experience:

```bash
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev
```

This creates a basic React project structure with all necessary configurations.

### Project Structure

A typical React project has this structure:

```
my-react-app/
├── node_modules/
├── public/
├── src/
│   ├── App.jsx
│   ├── App.css
│   ├── main.jsx
│   └── index.css
├── package.json
└── vite.config.js
```

The `src` folder contains your application code, with `main.jsx` as the entry point and `App.jsx` as the root component.

## Part 1: Fundamental Concepts

### Components

Components are the building blocks of React applications. They are reusable pieces of UI that can accept inputs (props) and maintain their own state.

#### Functional Components

Modern React uses functional components exclusively:

```javascript
function Welcome() {
  return <h1>Hello, React!</h1>;
}

export default Welcome;
```

#### JSX Syntax

JSX is a syntax extension that looks like HTML but is actually JavaScript:

```javascript
function UserCard() {
  const name = "Alice";
  const age = 28;

  return (
    <div className="card">
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Status: {age >= 18 ? "Adult" : "Minor"}</p>
    </div>
  );
}
```

Key JSX rules:
- Use `className` instead of `class`
- Use camelCase for attributes (onClick, onChange)
- All tags must be closed
- Return a single parent element (or use fragments)

#### Fragments

Fragments let you group multiple elements without adding extra DOM nodes:

```javascript
function List() {
  return (
    <>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </>
  );
}
```

### Props

Props (properties) are how components receive data from their parents:

```javascript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Jane" />
    </div>
  );
}
```

#### Destructuring Props

A cleaner approach uses destructuring:

```javascript
function UserProfile({ name, email, age }) {
  return (
    <div className="profile">
      <h2>{name}</h2>
      <p>Email: {email}</p>
      <p>Age: {age}</p>
    </div>
  );
}

function App() {
  return <UserProfile name="Alice" email="alice@example.com" age={30} />;
}
```

#### Default Props

Set default values for props:

```javascript
function Button({ text = "Click Me", type = "button" }) {
  return <button type={type}>{text}</button>;
}
```

### Practice Project 1: Product Card Component

Create a reusable product card:

```javascript
function ProductCard({ name, price, imageUrl, inStock = true }) {
  return (
    <div className="product-card">
      <img src={imageUrl} alt={name} />
      <h3>{name}</h3>
      <p className="price">${price.toFixed(2)}</p>
      <p className={inStock ? "in-stock" : "out-of-stock"}>
        {inStock ? "In Stock" : "Out of Stock"}
      </p>
      <button disabled={!inStock}>Add to Cart</button>
    </div>
  );
}

function App() {
  return (
    <div className="product-list">
      <ProductCard 
        name="Laptop" 
        price={999.99} 
        imageUrl="/laptop.jpg" 
        inStock={true}
      />
      <ProductCard 
        name="Headphones" 
        price={199.99} 
        imageUrl="/headphones.jpg" 
        inStock={false}
      />
    </div>
  );
}
```

## Part 2: State Management and Interactivity

### useState Hook

The `useState` hook adds state to functional components:

```javascript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

#### State Update Patterns

Always use the updater function for state based on previous state:

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount(prevCount => prevCount + 1);
  };

  const handleMultipleIncrements = () => {
    setCount(prevCount => prevCount + 1);
    setCount(prevCount => prevCount + 1);
    setCount(prevCount => prevCount + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleMultipleIncrements}>Add 3</button>
    </div>
  );
}
```

#### Complex State

State can hold objects and arrays:

```javascript
function UserForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    age: ''
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData(prevData => ({
      ...prevData,
      [name]: value
    }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Form submitted:', formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input 
        name="name" 
        value={formData.name} 
        onChange={handleChange} 
        placeholder="Name"
      />
      <input 
        name="email" 
        value={formData.email} 
        onChange={handleChange} 
        placeholder="Email"
      />
      <input 
        name="age" 
        value={formData.age} 
        onChange={handleChange} 
        placeholder="Age"
        type="number"
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

### Event Handling

React events use camelCase naming and pass synthetic events:

```javascript
function FormExample() {
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Form submitted');
  };

  const handleInputChange = (event) => {
    console.log('Input value:', event.target.value);
  };

  const handleKeyPress = (event) => {
    if (event.key === 'Enter') {
      console.log('Enter key pressed');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input 
        onChange={handleInputChange}
        onKeyPress={handleKeyPress}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

### Conditional Rendering

Render components based on conditions:

```javascript
function LoginControl() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  if (isLoggedIn) {
    return (
      <div>
        <h2>Welcome back!</h2>
        <button onClick={() => setIsLoggedIn(false)}>Logout</button>
      </div>
    );
  }

  return (
    <div>
      <h2>Please sign in</h2>
      <button onClick={() => setIsLoggedIn(true)}>Login</button>
    </div>
  );
}
```

Using ternary operators and logical AND:

```javascript
function Notification({ message, type }) {
  return (
    <div>
      {message && <p className={type}>{message}</p>}
      {type === 'error' ? <span>❌</span> : <span>✓</span>}
    </div>
  );
}
```

### Lists and Keys

Render arrays of data using map:

```javascript
function TodoList() {
  const [todos, setTodos] = useState([
    { id: 1, text: 'Learn React', completed: false },
    { id: 2, text: 'Build a project', completed: false }
  ]);

  const toggleTodo = (id) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  return (
    <ul>
      {todos.map(todo => (
        <li key={todo.id}>
          <input
            type="checkbox"
            checked={todo.completed}
            onChange={() => toggleTodo(todo.id)}
          />
          <span style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}>
            {todo.text}
          </span>
        </li>
      ))}
    </ul>
  );
}
```

Keys should be stable, unique identifiers. Never use array indices as keys when list items can be reordered.

### Practice Project 2: Todo Application

A complete todo app with add, toggle, and delete functionality:

```javascript
import { useState } from 'react';

function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const addTodo = () => {
    if (inputValue.trim() === '') return;

    const newTodo = {
      id: Date.now(),
      text: inputValue,
      completed: false
    };

    setTodos(prevTodos => [...prevTodos, newTodo]);
    setInputValue('');
  };

  const toggleTodo = (id) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id) => {
    setTodos(prevTodos => prevTodos.filter(todo => todo.id !== id));
  };

  const handleKeyPress = (e) => {
    if (e.key === 'Enter') {
      addTodo();
    }
  };

  return (
    <div className="todo-app">
      <h1>My Todo List</h1>
      <div className="input-section">
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          onKeyPress={handleKeyPress}
          placeholder="Enter a new todo"
        />
        <button onClick={addTodo}>Add</button>
      </div>
      <ul className="todo-list">
        {todos.map(todo => (
          <li key={todo.id} className="todo-item">
            <input
              type="checkbox"
              checked={todo.completed}
              onChange={() => toggleTodo(todo.id)}
            />
            <span className={todo.completed ? 'completed' : ''}>
              {todo.text}
            </span>
            <button onClick={() => deleteTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
      <p>Total: {todos.length} | Completed: {todos.filter(t => t.completed).length}</p>
    </div>
  );
}

export default TodoApp;
```

## Part 3: Side Effects and Lifecycle

### useEffect Hook

The `useEffect` hook handles side effects in functional components:

```javascript
import { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);

    return () => clearInterval(interval);
  }, []);

  return <div>Elapsed: {seconds} seconds</div>;
}
```

#### Dependency Array

The dependency array controls when effects run:

```javascript
function UserProfile({ userId }) {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch(`https://api.example.com/users/${userId}`)
      .then(res => res.json())
      .then(data => setUser(data));
  }, [userId]);

  if (!user) return <div>Loading...</div>;

  return <div>{user.name}</div>;
}
```

Dependency patterns:
- No array: runs after every render
- Empty array `[]`: runs once after initial render
- `[dep1, dep2]`: runs when dependencies change

#### Cleanup Functions

Always clean up side effects to prevent memory leaks:

```javascript
function WindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);

    window.addEventListener('resize', handleResize);

    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return <div>Window width: {width}px</div>;
}
```

### Data Fetching

Fetching data with useEffect:

```javascript
import { useState, useEffect } from 'react';

function PostsList() {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => {
        if (!response.ok) throw new Error('Failed to fetch');
        return response.json();
      })
      .then(data => {
        setPosts(data.slice(0, 10));
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  }, []);

  if (loading) return <div>Loading posts...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div>
      <h2>Posts</h2>
      <ul>
        {posts.map(post => (
          <li key={post.id}>
            <h3>{post.title}</h3>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

### Practice Project 3: Weather App

A weather application fetching data from an API:

```javascript
import { useState, useEffect } from 'react';

function WeatherApp() {
  const [city, setCity] = useState('London');
  const [weather, setWeather] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [inputValue, setInputValue] = useState('');

  const fetchWeather = (cityName) => {
    setLoading(true);
    setError(null);

    const API_KEY = 'your_api_key_here';
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${cityName}&appid=${API_KEY}&units=metric`;

    fetch(url)
      .then(res => {
        if (!res.ok) throw new Error('City not found');
        return res.json();
      })
      .then(data => {
        setWeather(data);
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  };

  useEffect(() => {
    fetchWeather(city);
  }, [city]);

  const handleSearch = () => {
    if (inputValue.trim()) {
      setCity(inputValue);
      setInputValue('');
    }
  };

  return (
    <div className="weather-app">
      <h1>Weather App</h1>
      <div className="search">
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Enter city name"
        />
        <button onClick={handleSearch}>Search</button>
      </div>

      {loading && <p>Loading weather data...</p>}
      {error && <p className="error">{error}</p>}

      {weather && !loading && (
        <div className="weather-info">
          <h2>{weather.name}, {weather.sys.country}</h2>
          <p className="temperature">{Math.round(weather.main.temp)}°C</p>
          <p className="description">{weather.weather[0].description}</p>
          <div className="details">
            <p>Humidity: {weather.main.humidity}%</p>
            <p>Wind Speed: {weather.wind.speed} m/s</p>
            <p>Pressure: {weather.main.pressure} hPa</p>
          </div>
        </div>
      )}
    </div>
  );
}

export default WeatherApp;
```

## Part 4: Advanced Hooks

### useRef Hook

`useRef` creates a mutable reference that persists across renders:

```javascript
import { useRef, useEffect } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} type="text" />;
}
```

Using useRef for tracking values without triggering re-renders:

```javascript
function RenderCounter() {
  const renderCount = useRef(0);

  useEffect(() => {
    renderCount.current += 1;
  });

  return <div>This component has rendered {renderCount.current} times</div>;
}
```

### useReducer Hook

`useReducer` manages complex state logic:

```javascript
import { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return initialState;
    case 'incrementBy':
      return { count: state.count + action.payload };
    default:
      throw new Error('Unknown action type');
  }
}

function CounterWithReducer() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+1</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-1</button>
      <button onClick={() => dispatch({ type: 'incrementBy', payload: 5 })}>+5</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </div>
  );
}
```

### useContext Hook

Context provides a way to pass data through the component tree without props drilling:

```javascript
import { createContext, useContext, useState } from 'react';

const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(prev => prev === 'light' ? 'dark' : 'light');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ThemedButton() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={toggleTheme}
      style={{
        background: theme === 'light' ? '#fff' : '#333',
        color: theme === 'light' ? '#333' : '#fff'
      }}
    >
      Toggle Theme (Current: {theme})
    </button>
  );
}

function App() {
  return (
    <ThemeProvider>
      <div>
        <h1>My App</h1>
        <ThemedButton />
      </div>
    </ThemeProvider>
  );
}
```

### useMemo Hook

`useMemo` memoizes expensive computations:

```javascript
import { useState, useMemo } from 'react';

function ExpensiveComponent({ numbers }) {
  const [multiplier, setMultiplier] = useState(1);

  const sum = useMemo(() => {
    console.log('Calculating sum...');
    return numbers.reduce((acc, num) => acc + num, 0);
  }, [numbers]);

  const result = sum * multiplier;

  return (
    <div>
      <p>Sum: {sum}</p>
      <p>Result: {result}</p>
      <button onClick={() => setMultiplier(m => m + 1)}>
        Increment Multiplier ({multiplier})
      </button>
    </div>
  );
}
```

### useCallback Hook

`useCallback` memoizes function references:

```javascript
import { useState, useCallback, memo } from 'react';

const Button = memo(({ onClick, label }) => {
  console.log(`Rendering button: ${label}`);
  return <button onClick={onClick}>{label}</button>;
});

function ParentComponent() {
  const [count, setCount] = useState(0);
  const [other, setOther] = useState(0);

  const incrementCount = useCallback(() => {
    setCount(c => c + 1);
  }, []);

  const incrementOther = useCallback(() => {
    setOther(o => o + 1);
  }, []);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Other: {other}</p>
      <Button onClick={incrementCount} label="Increment Count" />
      <Button onClick={incrementOther} label="Increment Other" />
    </div>
  );
}
```

### Custom Hooks

Create reusable logic with custom hooks:

```javascript
import { useState, useEffect } from 'react';

function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}

function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(handler);
  }, [value, delay]);

  return debouncedValue;
}

function SearchComponent() {
  const [searchTerm, setSearchTerm] = useLocalStorage('searchTerm', '');
  const debouncedSearchTerm = useDebounce(searchTerm, 500);

  useEffect(() => {
    if (debouncedSearchTerm) {
      console.log('Searching for:', debouncedSearchTerm);
    }
  }, [debouncedSearchTerm]);

  return (
    <input
      type="text"
      value={searchTerm}
      onChange={(e) => setSearchTerm(e.target.value)}
      placeholder="Search..."
    />
  );
}
```

### Practice Project 4: Shopping Cart with Context

A shopping cart using Context and useReducer:

```javascript
import { createContext, useContext, useReducer } from 'react';

const CartContext = createContext();

const cartReducer = (state, action) => {
  switch (action.type) {
    case 'ADD_ITEM':
      const existingItem = state.items.find(item => item.id === action.payload.id);
      if (existingItem) {
        return {
          ...state,
          items: state.items.map(item =>
            item.id === action.payload.id
              ? { ...item, quantity: item.quantity + 1 }
              : item
          )
        };
      }
      return {
        ...state,
        items: [...state.items, { ...action.payload, quantity: 1 }]
      };

    case 'REMOVE_ITEM':
      return {
        ...state,
        items: state.items.filter(item => item.id !== action.payload)
      };

    case 'UPDATE_QUANTITY':
      return {
        ...state,
        items: state.items.map(item =>
          item.id === action.payload.id
            ? { ...item, quantity: action.payload.quantity }
            : item
        )
      };

    case 'CLEAR_CART':
      return { items: [] };

    default:
      return state;
  }
};

function CartProvider({ children }) {
  const [state, dispatch] = useReducer(cartReducer, { items: [] });

  const addItem = (item) => dispatch({ type: 'ADD_ITEM', payload: item });
  const removeItem = (id) => dispatch({ type: 'REMOVE_ITEM', payload: id });
  const updateQuantity = (id, quantity) => 
    dispatch({ type: 'UPDATE_QUANTITY', payload: { id, quantity } });
  const clearCart = () => dispatch({ type: 'CLEAR_CART' });

  const total = state.items.reduce((sum, item) => sum + item.price * item.quantity, 0);
  const itemCount = state.items.reduce((sum, item) => sum + item.quantity, 0);

  return (
    <CartContext.Provider value={{
      items: state.items,
      addItem,
      removeItem,
      updateQuantity,
      clearCart,
      total,
      itemCount
    }}>
      {children}
    </CartContext.Provider>
  );
}

function useCart() {
  const context = useContext(CartContext);
  if (!context) {
    throw new Error('useCart must be used within CartProvider');
  }
  return context;
}

function ProductList() {
  const { addItem } = useCart();

  const products = [
    { id: 1, name: 'Laptop', price: 999 },
    { id: 2, name: 'Mouse', price: 29 },
    { id: 3, name: 'Keyboard', price: 79 }
  ];

  return (
    <div>
      <h2>Products</h2>
      {products.map(product => (
        <div key={product.id} className="product">
          <span>{product.name} - ${product.price}</span>
          <button onClick={() => addItem(product)}>Add to Cart</button>
        </div>
      ))}
    </div>
  );
}

function Cart() {
  const { items, removeItem, updateQuantity, clearCart, total, itemCount } = useCart();

  return (
    <div>
      <h2>Shopping Cart ({itemCount} items)</h2>
      {items.length === 0 ? (
        <p>Your cart is empty</p>
      ) : (
        <>
          {items.map(item => (
            <div key={item.id} className="cart-item">
              <span>{item.name}</span>
              <input
                type="number"
                min="1"
                value={item.quantity}
                onChange={(e) => updateQuantity(item.id, parseInt(e.target.value))}
              />
              <span>${item.price * item.quantity}</span>
              <button onClick={() => removeItem(item.id)}>Remove</button>
            </div>
          ))}
          <div className="cart-total">
            <strong>Total: ${total.toFixed(2)}</strong>
            <button onClick={clearCart}>Clear Cart</button>
          </div>
        </>
      )}
    </div>
  );
}

function App() {
  return (
    <CartProvider>
      <div>
        <h1>E-Commerce Store</h1>
        <ProductList />
        <Cart />
      </div>
    </CartProvider>
  );
}

export default App;
```

## Part 5: React Ecosystem and Libraries

### React Router

React Router enables navigation in single-page applications.

Installation:

```bash
npm install react-router-dom
```

Basic routing setup:

```javascript
import { BrowserRouter, Routes, Route, Link, useParams, useNavigate } from 'react-router-dom';

function Home() {
  return (
    <div>
      <h2>Home Page</h2>
      <p>Welcome to our application</p>
    </div>
  );
}

function About() {
  return (
    <div>
      <h2>About Page</h2>
      <p>This is the about page</p>
    </div>
  );
}

function UserProfile() {
  const { userId } = useParams();
  return <h2>User Profile: {userId}</h2>;
}

function Products() {
  const navigate = useNavigate();

  const goToProduct = (id) => {
    navigate(`/product/${id}`);
  };

  return (
    <div>
      <h2>Products</h2>
      <button onClick={() => goToProduct(1)}>View Product 1</button>
      <button onClick={() => goToProduct(2)}>View Product 2</button>
    </div>
  );
}

function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}

function Navigation() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
      <Link to="/user/123">User Profile</Link>
      <Link to="/products">Products</Link>
    </nav>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Navigation />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/user/:userId" element={<UserProfile />} />
        <Route path="/products" element={<Products />} />
        <Route path="/product/:productId" element={<UserProfile />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```

Protected routes pattern:

```javascript
import { Navigate } from 'react-router-dom';

function ProtectedRoute({ children, isAuthenticated }) {
  if (!isAuthenticated) {
    return <Navigate to="/login" replace />;
  }
  return children;
}

function App() {
  const [isAuthenticated, setIsAuthenticated] = useState(false);

  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login setAuth={setIsAuthenticated} />} />
        <Route
          path="/dashboard"
          element={
            <ProtectedRoute isAuthenticated={isAuthenticated}>
              <Dashboard />
            </ProtectedRoute>
          }
        />
      </Routes>
    </BrowserRouter>
  );
}
```

### Axios for HTTP Requests

Axios is a popular HTTP client with better features than fetch.

Installation:

```bash
npm install axios
```

Basic usage:

```javascript
import { useState, useEffect } from 'react';
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://jsonplaceholder.typicode.com',
  timeout: 5000,
  headers: {
    'Content-Type': 'application/json'
  }
});

function UsersList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    api.get('/users')
      .then(response => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  }, []);

  const createUser = async (userData) => {
    try {
      const response = await api.post('/users', userData);
      setUsers([...users, response.data]);
    } catch (err) {
      console.error('Error creating user:', err);
    }
  };

  const updateUser = async (id, userData) => {
    try {
      const response = await api.put(`/users/${id}`, userData);
      setUsers(users.map(user => user.id === id ? response.data : user));
    } catch (err) {
      console.error('Error updating user:', err);
    }
  };

  const deleteUser = async (id) => {
    try {
      await api.delete(`/users/${id}`);
      setUsers(users.filter(user => user.id !== id));
    } catch (err) {
      console.error('Error deleting user:', err);
    }
  };

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div>
      {users.map(user => (
        <div key={user.id}>
          <h3>{user.name}</h3>
          <button onClick={() => deleteUser(user.id)}>Delete</button>
        </div>
      ))}
    </div>
  );
}
```

### React Query (TanStack Query)

React Query provides powerful data fetching and caching capabilities.

Installation:

```bash
npm install @tanstack/react-query
```

Setup and usage:

```javascript
import { QueryClient, QueryClientProvider, useQuery, useMutation, useQueryClient } from '@tanstack/react-query';
import axios from 'axios';

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 5 * 60 * 1000,
      cacheTime: 10 * 60 * 1000,
      refetchOnWindowFocus: false
    }
  }
});

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <PostsComponent />
    </QueryClientProvider>
  );
}

const fetchPosts = async () => {
  const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts');
  return data;
};

const createPost = async (newPost) => {
  const { data } = await axios.post('https://jsonplaceholder.typicode.com/posts', newPost);
  return data;
};

function PostsComponent() {
  const queryClient = useQueryClient();

  const { data: posts, isLoading, isError, error } = useQuery({
    queryKey: ['posts'],
    queryFn: fetchPosts
  });

  const mutation = useMutation({
    mutationFn: createPost,
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ['posts'] });
    }
  });

  const handleCreatePost = () => {
    mutation.mutate({
      title: 'New Post',
      body: 'This is a new post',
      userId: 1
    });
  };

  if (isLoading) return <div>Loading posts...</div>;
  if (isError) return <div>Error: {error.message}</div>;

  return (
    <div>
      <button onClick={handleCreatePost} disabled={mutation.isLoading}>
        {mutation.isLoading ? 'Creating...' : 'Create Post'}
      </button>
      {posts.slice(0, 10).map(post => (
        <div key={post.id}>
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </div>
      ))}
    </div>
  );
}
```

Advanced React Query patterns:

```javascript
function PostDetails({ postId }) {
  const { data: post, isLoading } = useQuery({
    queryKey: ['post', postId],
    queryFn: async () => {
      const { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts/${postId}`);
      return data;
    },
    enabled: !!postId
  });

  const { data: comments } = useQuery({
    queryKey: ['comments', postId],
    queryFn: async () => {
      const { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts/${postId}/comments`);
      return data;
    },
    enabled: !!postId
  });

  if (isLoading) return <div>Loading...</div>;

  return (
    <div>
      <h2>{post.title}</h2>
      <p>{post.body}</p>
      <h3>Comments ({comments?.length || 0})</h3>
      {comments?.map(comment => (
        <div key={comment.id}>{comment.body}</div>
      ))}
    </div>
  );
}
```

### Zustand for State Management

Zustand is a lightweight state management solution.

Installation:

```bash
npm install zustand
```

Creating and using stores:

```javascript
import { create } from 'zustand';

const useUserStore = create((set) => ({
  user: null,
  isAuthenticated: false,
  login: (userData) => set({ user: userData, isAuthenticated: true }),
  logout: () => set({ user: null, isAuthenticated: false }),
  updateUser: (updates) => set((state) => ({
    user: { ...state.user, ...updates }
  }))
}));

const useTodoStore = create((set) => ({
  todos: [],
  addTodo: (todo) => set((state) => ({
    todos: [...state.todos, { id: Date.now(), ...todo }]
  })),
  removeTodo: (id) => set((state) => ({
    todos: state.todos.filter(todo => todo.id !== id)
  })),
  toggleTodo: (id) => set((state) => ({
    todos: state.todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    )
  }))
}));

function TodoApp() {
  const { todos, addTodo, removeTodo, toggleTodo } = useTodoStore();
  const [input, setInput] = useState('');

  const handleAdd = () => {
    if (input.trim()) {
      addTodo({ text: input, completed: false });
      setInput('');
    }
  };

  return (
    <div>
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      <button onClick={handleAdd}>Add</button>
      <ul>
        {todos.map(todo => (
          <li key={todo.id}>
            <input
              type="checkbox"
              checked={todo.completed}
              onChange={() => toggleTodo(todo.id)}
            />
            <span>{todo.text}</span>
            <button onClick={() => removeTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

function UserProfile() {
  const { user, isAuthenticated, login, logout } = useUserStore();

  if (!isAuthenticated) {
    return <button onClick={() => login({ name: 'John Doe', email: 'john@example.com' })}>
      Login
    </button>;
  }

  return (
    <div>
      <h2>{user.name}</h2>
      <p>{user.email}</p>
      <button onClick={logout}>Logout</button>
    </div>
  );
}
```

Zustand with persistence:

```javascript
import { create } from 'zustand';
import { persist } from 'zustand/middleware';

const useStore = create(
  persist(
    (set) => ({
      theme: 'light',
      setTheme: (theme) => set({ theme }),
      preferences: {},
      updatePreferences: (prefs) => set((state) => ({
        preferences: { ...state.preferences, ...prefs }
      }))
    }),
    {
      name: 'app-storage'
    }
  )
);
```

### Styling with Tailwind CSS

Tailwind CSS is a utility-first CSS framework.

Installation:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Configure `tailwind.config.js`:

```javascript
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Add to your CSS file:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Using Tailwind in components:

```javascript
function Card({ title, description, image }) {
  return (
    <div className="max-w-sm rounded overflow-hidden shadow-lg bg-white">
      <img className="w-full" src={image} alt={title} />
      <div className="px-6 py-4">
        <div className="font-bold text-xl mb-2">{title}</div>
        <p className="text-gray-700 text-base">{description}</p>
      </div>
      <div className="px-6 pt-4 pb-2">
        <button className="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
          Learn More
        </button>
      </div>
    </div>
  );
}

function Layout({ children }) {
  return (
    <div className="min-h-screen bg-gray-100">
      <nav className="bg-white shadow-lg">
        <div className="max-w-6xl mx-auto px-4">
          <div className="flex justify-between items-center py-4">
            <h1 className="text-2xl font-bold text-gray-800">My App</h1>
            <div className="flex space-x-4">
              <a href="/" className="text-gray-600 hover:text-gray-900">Home</a>
              <a href="/about" className="text-gray-600 hover:text-gray-900">About</a>
            </div>
          </div>
        </div>
      </nav>
      <main className="max-w-6xl mx-auto px-4 py-8">
        {children}
      </main>
    </div>
  );
}
```

### Styled Components

Styled Components allows writing CSS in JavaScript.

Installation:

```bash
npm install styled-components
```

Usage:

```javascript
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${props => props.primary ? '#007bff' : '#6c757d'};
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;

  &:hover {
    background-color: ${props => props.primary ? '#0056b3' : '#5a6268'};
  }

  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }
`;

const Card = styled.div`
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  margin: 10px 0;
`;

const Title = styled.h2`
  color: ${props => props.theme.primaryColor};
  font-size: 24px;
  margin-bottom: 10px;
`;

const Container = styled.div`
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;

  @media (max-width: 768px) {
    padding: 10px;
  }
`;

function StyledComponent() {
  return (
    <Container>
      <Card>
        <Title>Welcome</Title>
        <p>This is a styled component</p>
        <Button primary>Primary Button</Button>
        <Button>Secondary Button</Button>
      </Card>
    </Container>
  );
}
```

## Part 6: Performance Optimization

### React.memo

`React.memo` prevents unnecessary re-renders of components:

```javascript
import { memo } from 'react';

const ExpensiveComponent = memo(function ExpensiveComponent({ data, onUpdate }) {
  console.log('ExpensiveComponent rendered');

  return (
    <div>
      <h3>{data.title}</h3>
      <button onClick={onUpdate}>Update</button>
    </div>
  );
});

function ParentComponent() {
  const [count, setCount] = useState(0);
  const [data, setData] = useState({ title: 'Hello' });

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment: {count}</button>
      <ExpensiveComponent data={data} onUpdate={() => setData({ title: 'Updated' })} />
    </div>
  );
}
```

Custom comparison function:

```javascript
const MyComponent = memo(
  function MyComponent({ items }) {
    return <div>{items.length} items</div>;
  },
  (prevProps, nextProps) => {
    return prevProps.items.length === nextProps.items.length;
  }
);
```

### Code Splitting and Lazy Loading

Split your bundle for better initial load performance:

```javascript
import { lazy, Suspense } from 'react';

const Dashboard = lazy(() => import('./Dashboard'));
const Profile = lazy(() => import('./Profile'));
const Settings = lazy(() => import('./Settings'));

function App() {
  return (
    <BrowserRouter>
      <Suspense fallback={<div>Loading...</div>}>
        <Routes>
          <Route path="/dashboard" element={<Dashboard />} />
          <Route path="/profile" element={<Profile />} />
          <Route path="/settings" element={<Settings />} />
        </Routes>
      </Suspense>
    </BrowserRouter>
  );
}
```

Component-level lazy loading:

```javascript
function TabsComponent() {
  const [activeTab, setActiveTab] = useState('home');

  const HomeTab = lazy(() => import('./tabs/HomeTab'));
  const ProfileTab = lazy(() => import('./tabs/ProfileTab'));
  const SettingsTab = lazy(() => import('./tabs/SettingsTab'));

  return (
    <div>
      <div className="tabs">
        <button onClick={() => setActiveTab('home')}>Home</button>
        <button onClick={() => setActiveTab('profile')}>Profile</button>
        <button onClick={() => setActiveTab('settings')}>Settings</button>
      </div>
      <Suspense fallback={<div>Loading tab...</div>}>
        {activeTab === 'home' && <HomeTab />}
        {activeTab === 'profile' && <ProfileTab />}
        {activeTab === 'settings' && <SettingsTab />}
      </Suspense>
    </div>
  );
}
```

### Virtualization for Long Lists

Install react-window for efficient list rendering:

```bash
npm install react-window
```

Usage:

```javascript
import { FixedSizeList } from 'react-window';

function VirtualizedList() {
  const items = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);

  const Row = ({ index, style }) => (
    <div style={style} className="list-item">
      {items[index]}
    </div>
  );

  return (
    <FixedSizeList
      height={600}
      itemCount={items.length}
      itemSize={50}
      width="100%"
    >
      {Row}
    </FixedSizeList>
  );
}
```

### Debouncing and Throttling

Optimize event handlers:

```javascript
import { useState, useCallback } from 'react';

function useDebounce(callback, delay) {
  const [timeoutId, setTimeoutId] = useState(null);

  return useCallback((...args) => {
    if (timeoutId) clearTimeout(timeoutId);

    const newTimeoutId = setTimeout(() => {
      callback(...args);
    }, delay);

    setTimeoutId(newTimeoutId);
  }, [callback, delay, timeoutId]);
}

function SearchWithDebounce() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);

  const searchAPI = async (searchTerm) => {
    console.log('Searching for:', searchTerm);
    const response = await fetch(`https://api.example.com/search?q=${searchTerm}`);
    const data = await response.json();
    setResults(data);
  };

  const debouncedSearch = useDebounce(searchAPI, 500);

  const handleInputChange = (e) => {
    const value = e.target.value;
    setQuery(value);
    debouncedSearch(value);
  };

  return (
    <div>
      <input
        type="text"
        value={query}
        onChange={handleInputChange}
        placeholder="Search..."
      />
      <div>
        {results.map((result, index) => (
          <div key={index}>{result.name}</div>
        ))}
      </div>
    </div>
  );
}
```

## Part 7: Forms and Validation

### Controlled Components

Handling form inputs:

```javascript
function RegistrationForm() {
  const [formData, setFormData] = useState({
    username: '',
    email: '',
    password: '',
    confirmPassword: '',
    agreeToTerms: false
  });

  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));
  };

  const validate = () => {
    const newErrors = {};

    if (!formData.username || formData.username.length < 3) {
      newErrors.username = 'Username must be at least 3 characters';
    }

    if (!formData.email || !/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Please enter a valid email';
    }

    if (!formData.password || formData.password.length < 6) {
      newErrors.password = 'Password must be at least 6 characters';
    }

    if (formData.password !== formData.confirmPassword) {
      newErrors.confirmPassword = 'Passwords do not match';
    }

    if (!formData.agreeToTerms) {
      newErrors.agreeToTerms = 'You must agree to the terms';
    }

    return newErrors;
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    const validationErrors = validate();

    if (Object.keys(validationErrors).length > 0) {
      setErrors(validationErrors);
      return;
    }

    console.log('Form submitted:', formData);
    setErrors({});
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <input
          type="text"
          name="username"
          value={formData.username}
          onChange={handleChange}
          placeholder="Username"
        />
        {errors.username && <span className="error">{errors.username}</span>}
      </div>

      <div>
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
          placeholder="Email"
        />
        {errors.email && <span className="error">{errors.email}</span>}
      </div>

      <div>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleChange}
          placeholder="Password"
        />
        {errors.password && <span className="error">{errors.password}</span>}
      </div>

      <div>
        <input
          type="password"
          name="confirmPassword"
          value={formData.confirmPassword}
          onChange={handleChange}
          placeholder="Confirm Password"
        />
        {errors.confirmPassword && <span className="error">{errors.confirmPassword}</span>}
      </div>

      <div>
        <label>
          <input
            type="checkbox"
            name="agreeToTerms"
            checked={formData.agreeToTerms}
            onChange={handleChange}
          />
          I agree to the terms and conditions
        </label>
        {errors.agreeToTerms && <span className="error">{errors.agreeToTerms}</span>}
      </div>

      <button type="submit">Register</button>
    </form>
  );
}
```

### React Hook Form

A performant form library with minimal re-renders.

Installation:

```bash
npm install react-hook-form
```

Usage:

```javascript
import { useForm } from 'react-hook-form';

function LoginForm() {
  const {
    register,
    handleSubmit,
    formState: { errors, isSubmitting }
  } = useForm({
    defaultValues: {
      email: '',
      password: ''
    }
  });

  const onSubmit = async (data) => {
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log('Form data:', data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <input
          {...register('email', {
            required: 'Email is required',
            pattern: {
              value: /\S+@\S+\.\S+/,
              message: 'Invalid email format'
            }
          })}
          placeholder="Email"
        />
        {errors.email && <span className="error">{errors.email.message}</span>}
      </div>

      <div>
        <input
          type="password"
          {...register('password', {
            required: 'Password is required',
            minLength: {
              value: 6,
              message: 'Password must be at least 6 characters'
            }
          })}
          placeholder="Password"
        />
        {errors.password && <span className="error">{errors.password.message}</span>}
      </div>

      <button type="submit" disabled={isSubmitting}>
        {isSubmitting ? 'Logging in...' : 'Login'}
      </button>
    </form>
  );
}
```

Advanced React Hook Form with validation:

```javascript
import { useForm, Controller } from 'react-hook-form';

function ComplexForm() {
  const {
    register,
    handleSubmit,
    watch,
    control,
    formState: { errors }
  } = useForm();

  const password = watch('password');

  const onSubmit = (data) => {
    console.log('Valid form data:', data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        {...register('username', {
          required: 'Username is required',
          minLength: {
            value: 3,
            message: 'Minimum 3 characters'
          },
          validate: async (value) => {
            const isAvailable = await checkUsernameAvailability(value);
            return isAvailable || 'Username is taken';
          }
        })}
        placeholder="Username"
      />
      {errors.username && <span>{errors.username.message}</span>}

      <input
        type="password"
        {...register('password', {
          required: 'Password is required',
          minLength: { value: 8, message: 'Minimum 8 characters' }
        })}
        placeholder="Password"
      />
      {errors.password && <span>{errors.password.message}</span>}

      <input
        type="password"
        {...register('confirmPassword', {
          required: 'Please confirm password',
          validate: value => value === password || 'Passwords do not match'
        })}
        placeholder="Confirm Password"
      />
      {errors.confirmPassword && <span>{errors.confirmPassword.message}</span>}

      <select {...register('country', { required: 'Country is required' })}>
        <option value="">Select country</option>
        <option value="us">United States</option>
        <option value="uk">United Kingdom</option>
        <option value="ca">Canada</option>
      </select>
      {errors.country && <span>{errors.country.message}</span>}

      <button type="submit">Submit</button>
    </form>
  );
}

async function checkUsernameAvailability(username) {
  await new Promise(resolve => setTimeout(resolve, 500));
  return username !== 'admin';
}
```

## Part 8: Testing React Applications

### Testing with Vitest and React Testing Library

Installation:

```bash
npm install -D vitest @testing-library/react @testing-library/jest-dom @testing-library/user-event jsdom
```

Configure `vite.config.js`:

```javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: './src/test/setup.js'
  }
});
```

Create `src/test/setup.js`:

```javascript
import '@testing-library/jest-dom';
```

Component testing:

```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import { describe, it, expect, vi } from 'vitest';
import Counter from './Counter';

describe('Counter Component', () => {
  it('renders initial count', () => {
    render(<Counter />);
    expect(screen.getByText(/count: 0/i)).toBeInTheDocument();
  });

  it('increments count when button clicked', () => {
    render(<Counter />);
    const button = screen.getByText(/increment/i);
    fireEvent.click(button);
    expect(screen.getByText(/count: 1/i)).toBeInTheDocument();
  });

  it('calls onIncrement callback', () => {
    const mockCallback = vi.fn();
    render(<Counter onIncrement={mockCallback} />);
    const button = screen.getByText(/increment/i);
    fireEvent.click(button);
    expect(mockCallback).toHaveBeenCalledTimes(1);
  });
});
```

Testing async operations:

```javascript
import { render, screen, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import { describe, it, expect, vi } from 'vitest';

describe('UserProfile', () => {
  it('fetches and displays user data', async () => {
    global.fetch = vi.fn(() =>
      Promise.resolve({
        json: () => Promise.resolve({ name: 'John Doe', email: 'john@example.com' })
      })
    );

    render(<UserProfile userId={1} />);

    expect(screen.getByText(/loading/i)).toBeInTheDocument();

    await waitFor(() => {
      expect(screen.getByText('John Doe')).toBeInTheDocument();
    });

    expect(screen.getByText('john@example.com')).toBeInTheDocument();
  });
});
```

## Part 9: Advanced Patterns and Best Practices

### Component Composition

Use composition over inheritance:

```javascript
function Card({ children, variant = 'default' }) {
  const className = `card card-${variant}`;
  return <div className={className}>{children}</div>;
}

function CardHeader({ children }) {
  return <div className="card-header">{children}</div>;
}

function CardBody({ children }) {
  return <div className="card-body">{children}</div>;
}

function CardFooter({ children }) {
  return <div className="card-footer">{children}</div>;
}

Card.Header = CardHeader;
Card.Body = CardBody;
Card.Footer = CardFooter;

function Example() {
  return (
    <Card variant="primary">
      <Card.Header>
        <h2>Title</h2>
      </Card.Header>
      <Card.Body>
        <p>Content goes here</p>
      </Card.Body>
      <Card.Footer>
        <button>Action</button>
      </Card.Footer>
    </Card>
  );
}
```

### Render Props Pattern

Share code between components:

```javascript
function MouseTracker({ render }) {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  useEffect(() => {
    const handleMouseMove = (event) => {
      setPosition({ x: event.clientX, y: event.clientY });
    };

    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  return render(position);
}

function App() {
  return (
    <MouseTracker
      render={({ x, y }) => (
        <div>
          <h2>Mouse position:</h2>
          <p>X: {x}, Y: {y}</p>
        </div>
      )}
    />
  );
}
```

### Higher-Order Components

Enhance components with additional functionality:

```javascript
function withLoading(Component) {
  return function WithLoadingComponent({ isLoading, ...props }) {
    if (isLoading) {
      return <div>Loading...</div>;
    }
    return <Component {...props} />;
  };
}

function withAuth(Component) {
  return function WithAuthComponent(props) {
    const { isAuthenticated } = useAuth();

    if (!isAuthenticated) {
      return <Navigate to="/login" />;
    }

    return <Component {...props} />;
  };
}

function UserList({ users }) {
  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  );
}

const UserListWithLoading = withLoading(UserList);
const ProtectedUserList = withAuth(UserListWithLoading);
```

### Error Boundaries

Catch and handle errors in component trees:

```javascript
import { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }

  componentDidCatch(error, errorInfo) {
    console.error('Error caught by boundary:', error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return (
        <div className="error-boundary">
          <h2>Something went wrong</h2>
          <p>{this.state.error?.message}</p>
          <button onClick={() => this.setState({ hasError: false })}>
            Try again
          </button>
        </div>
      );
    }

    return this.props.children;
  }
}

function App() {
  return (
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
  );
}
```

### Compound Components Pattern

Create components that work together seamlessly:

```javascript
import { createContext, useContext, useState } from 'react';

const TabsContext = createContext();

function Tabs({ children, defaultTab }) {
  const [activeTab, setActiveTab] = useState(defaultTab);

  return (
    <TabsContext.Provider value={{ activeTab, setActiveTab }}>
      <div className="tabs">{children}</div>
    </TabsContext.Provider>
  );
}

function TabList({ children }) {
  return <div className="tab-list">{children}</div>;
}

function Tab({ id, children }) {
  const { activeTab, setActiveTab } = useContext(TabsContext);
  const isActive = activeTab === id;

  return (
    <button
      className={`tab ${isActive ? 'active' : ''}`}
      onClick={() => setActiveTab(id)}
    >
      {children}
    </button>
  );
}

function TabPanels({ children }) {
  return <div className="tab-panels">{children}</div>;
}

function TabPanel({ id, children }) {
  const { activeTab } = useContext(TabsContext);

  if (activeTab !== id) return null;

  return <div className="tab-panel">{children}</div>;
}

Tabs.List = TabList;
Tabs.Tab = Tab;
Tabs.Panels = TabPanels;
Tabs.Panel = TabPanel;

function Example() {
  return (
    <Tabs defaultTab="home">
      <Tabs.List>
        <Tabs.Tab id="home">Home</Tabs.Tab>
        <Tabs.Tab id="profile">Profile</Tabs.Tab>
        <Tabs.Tab id="settings">Settings</Tabs.Tab>
      </Tabs.List>

      <Tabs.Panels>
        <Tabs.Panel id="home">
          <h2>Home Content</h2>
        </Tabs.Panel>
        <Tabs.Panel id="profile">
          <h2>Profile Content</h2>
        </Tabs.Panel>
        <Tabs.Panel id="settings">
          <h2>Settings Content</h2>
        </Tabs.Panel>
      </Tabs.Panels>
    </Tabs>
  );
}
```

## Part 10: Final Project - Blog Application

A complete blog application combining all concepts:

```javascript
import { BrowserRouter, Routes, Route, Link, useParams, useNavigate } from 'react-router-dom';
import { QueryClient, QueryClientProvider, useQuery, useMutation, useQueryClient } from '@tanstack/react-query';
import { create } from 'zustand';
import axios from 'axios';
import { useState } from 'react';

const queryClient = new QueryClient();

const api = axios.create({
  baseURL: 'https://jsonplaceholder.typicode.com'
});

const useAuthStore = create((set) => ({
  user: null,
  isAuthenticated: false,
  login: (user) => set({ user, isAuthenticated: true }),
  logout: () => set({ user: null, isAuthenticated: false })
}));

function BlogApp() {
  return (
    <QueryClientProvider client={queryClient}>
      <BrowserRouter>
        <div className="blog-app">
          <Navigation />
          <main className="container">
            <Routes>
              <Route path="/" element={<Home />} />
              <Route path="/posts" element={<PostsList />} />
              <Route path="/posts/:id" element={<PostDetail />} />
              <Route path="/create" element={<CreatePost />} />
              <Route path="/login" element={<Login />} />
            </Routes>
          </main>
        </div>
      </BrowserRouter>
    </QueryClientProvider>
  );
}

function Navigation() {
  const { isAuthenticated, user, logout } = useAuthStore();

  return (
    <nav className="navbar">
      <div className="nav-brand">
        <Link to="/">My Blog</Link>
      </div>
      <div className="nav-links">
        <Link to="/posts">All Posts</Link>
        {isAuthenticated ? (
          <>
            <Link to="/create">Create Post</Link>
            <span>Welcome, {user.name}</span>
            <button onClick={logout}>Logout</button>
          </>
        ) : (
          <Link to="/login">Login</Link>
        )}
      </div>
    </nav>
  );
}

function Home() {
  return (
    <div className="home">
      <h1>Welcome to My Blog</h1>
      <p>Discover amazing articles and stories</p>
      <Link to="/posts" className="btn-primary">
        Browse Posts
      </Link>
    </div>
  );
}

function PostsList() {
  const [page, setPage] = useState(1);
  const postsPerPage = 10;

  const { data: posts, isLoading, isError } = useQuery({
    queryKey: ['posts'],
    queryFn: async () => {
      const { data } = await api.get('/posts');
      return data;
    }
  });

  if (isLoading) return <div className="loading">Loading posts...</div>;
  if (isError) return <div className="error">Failed to load posts</div>;

  const totalPages = Math.ceil(posts.length / postsPerPage);
  const startIndex = (page - 1) * postsPerPage;
  const currentPosts = posts.slice(startIndex, startIndex + postsPerPage);

  return (
    <div className="posts-list">
      <h1>All Posts</h1>
      <div className="posts-grid">
        {currentPosts.map(post => (
          <PostCard key={post.id} post={post} />
        ))}
      </div>
      <Pagination
        currentPage={page}
        totalPages={totalPages}
        onPageChange={setPage}
      />
    </div>
  );
}

function PostCard({ post }) {
  return (
    <Link to={`/posts/${post.id}`} className="post-card">
      <h3>{post.title}</h3>
      <p>{post.body.substring(0, 100)}...</p>
      <span className="read-more">Read more</span>
    </Link>
  );
}

function PostDetail() {
  const { id } = useParams();

  const { data: post, isLoading: postLoading } = useQuery({
    queryKey: ['post', id],
    queryFn: async () => {
      const { data } = await api.get(`/posts/${id}`);
      return data;
    }
  });

  const { data: comments } = useQuery({
    queryKey: ['comments', id],
    queryFn: async () => {
      const { data } = await api.get(`/posts/${id}/comments`);
      return data;
    }
  });

  const { data: author } = useQuery({
    queryKey: ['user', post?.userId],
    queryFn: async () => {
      const { data } = await api.get(`/users/${post.userId}`);
      return data;
    },
    enabled: !!post?.userId
  });

  if (postLoading) return <div className="loading">Loading post...</div>;

  return (
    <div className="post-detail">
      <article>
        <h1>{post.title}</h1>
        {author && (
          <div className="author-info">
            <span>By {author.name}</span>
            <span>{author.email}</span>
          </div>
        )}
        <div className="post-body">
          <p>{post.body}</p>
        </div>
      </article>

      <section className="comments">
        <h2>Comments ({comments?.length || 0})</h2>
        {comments?.map(comment => (
          <div key={comment.id} className="comment">
            <h4>{comment.name}</h4>
            <p className="comment-email">{comment.email}</p>
            <p>{comment.body}</p>
          </div>
        ))}
      </section>
    </div>
  );
}

function CreatePost() {
  const [formData, setFormData] = useState({
    title: '',
    body: ''
  });
  const navigate = useNavigate();
  const queryClient = useQueryClient();
  const { isAuthenticated } = useAuthStore();

  const mutation = useMutation({
    mutationFn: async (newPost) => {
      const { data } = await api.post('/posts', newPost);
      return data;
    },
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ['posts'] });
      navigate('/posts');
    }
  });

  if (!isAuthenticated) {
    return <div>Please login to create a post</div>;
  }

  const handleSubmit = (e) => {
    e.preventDefault();
    mutation.mutate({
      ...formData,
      userId: 1
    });
  };

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  return (
    <div className="create-post">
      <h1>Create New Post</h1>
      <form onSubmit={handleSubmit}>
        <div className="form-group">
          <label>Title</label>
          <input
            type="text"
            name="title"
            value={formData.title}
            onChange={handleChange}
            required
          />
        </div>

        <div className="form-group">
          <label>Content</label>
          <textarea
            name="body"
            value={formData.body}
            onChange={handleChange}
            rows="10"
            required
          />
        </div>

        <button type="submit" disabled={mutation.isLoading}>
          {mutation.isLoading ? 'Publishing...' : 'Publish Post'}
        </button>

        {mutation.isError && (
          <div className="error">Failed to create post</div>
        )}
      </form>
    </div>
  );
}

function Login() {
  const [email, setEmail] = useState('');
  const { login } = useAuthStore();
  const navigate = useNavigate();

  const handleSubmit = (e) => {
    e.preventDefault();
    login({ name: 'Demo User', email });
    navigate('/');
  };

  return (
    <div className="login">
      <h1>Login</h1>
      <form onSubmit={handleSubmit}>
        <input
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          placeholder="Enter your email"
          required
        />
        <button type="submit">Login</button>
      </form>
    </div>
  );
}

function Pagination({ currentPage, totalPages, onPageChange }) {
  return (
    <div className="pagination">
      <button
        onClick={() => onPageChange(currentPage - 1)}
        disabled={currentPage === 1}
      >
        Previous
      </button>
      <span>Page {currentPage} of {totalPages}</span>
      <button
        onClick={() => onPageChange(currentPage + 1)}
        disabled={currentPage === totalPages}
      >
        Next
      </button>
    </div>
  );
}

export default BlogApp;
```

## Best Practices Summary

### Component Organization

- Keep components small and focused on a single responsibility
- Extract reusable logic into custom hooks
- Use composition over inheritance
- Organize files by feature rather than type

### State Management

- Keep state as local as possible
- Lift state up only when necessary
- Use Context for global state that changes infrequently
- Consider Zustand or Redux for complex state
- Track active items by ID, not entire objects

### Performance

- Use React.memo for expensive components
- Memoize callbacks with useCallback
- Memoize expensive calculations with useMemo
- Implement code splitting with lazy loading
- Avoid inline function definitions in render
- Use production builds for deployment

### Code Quality

- Use TypeScript for type safety in large applications
- Write meaningful component and prop names
- Keep useEffect simple with one concern per effect
- Always clean up side effects
- Avoid mutating state directly
- Use ESLint and Prettier for code consistency

### Data Fetching

- Use React Query or SWR for server state
- Handle loading and error states
- Implement proper error boundaries
- Cache and deduplicate requests
- Consider using optimistic updates

### Styling

- Choose one styling approach and stick with it
- Use CSS modules or styled-components for component scoping
- Consider Tailwind CSS for utility-first approach
- Keep styles colocated with components
- Use CSS variables for theming

### Testing

- Write tests for critical business logic
- Test user interactions, not implementation details
- Use React Testing Library for component tests
- Mock external dependencies
- Aim for meaningful test coverage

## Conclusion

This tutorial covered React from fundamentals to advanced patterns. You learned about components, hooks, state management, routing, data fetching, styling, performance optimization, and testing. By building the practice projects, you gained hands-on experience with real-world scenarios. Continue practicing by building your own projects, exploring the React ecosystem, and staying updated with the latest React features and best practices. The React community is vast and helpful, so do not hesitate to seek help when needed. Happy coding!
