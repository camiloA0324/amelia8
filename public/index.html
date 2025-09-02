import React, { useState, useEffect, createContext, useContext } from 'react';
import { User, Package, ShoppingCart, DollarSign, Users, LogOut, Menu, X, Plus, Trash2, Edit, Save, FileText, TrendingUp, AlertCircle, Check, Wifi, WifiOff, RefreshCw, Lock, Unlock, Building } from 'lucide-react';

// ============================================
// CONFIGURACIÓN DE FIREBASE
// ============================================
// IMPORTANTE: Reemplaza estos valores con tu configuración de Firebase
const firebaseConfig = {
  apiKey: "TU-API-KEY",
  authDomain: "TU-AUTH-DOMAIN",
  projectId: "TU-PROJECT-ID",
  storageBucket: "TU-STORAGE-BUCKET",
  messagingSenderId: "TU-MESSAGING-SENDER-ID",
  appId: "TU-APP-ID"
};

// Context para manejo global de estado
const AppContext = createContext();
const useApp = () => useContext(AppContext);

// ============================================
// SERVICIO DE FIREBASE (Simulado para Demo)
// ============================================
class FirebaseService {
  constructor() {
    this.isOnline = true;
    this.listeners = [];
    this.auth = null;
    this.db = null;
    
    // Simular datos locales para demo
    this.localData = {
      users: [
        { 
          id: '1', 
          email: 'AmeliA@sistema.com', 
          password: 'Camilo123', 
          role: 'superadmin', 
          name: 'Amelia Admin',
          isBlocked: false,
          createdAt: new Date().toISOString() 
        },
        { 
          id: '2', 
          email: 'zapateria1@amelia.com', 
          password: 'zapatos123', 
          role: 'owner', 
          name: 'Juan Pérez', 
          businessName: 'Zapatería El Paso',
          ownerId: null,
          isBlocked: false,
          createdAt: new Date().toISOString() 
        },
        { 
          id: '3', 
          email: 'vendedor1@amelia.com', 
          password: 'venta123', 
          role: 'seller', 
          name: 'María García', 
          ownerId: '2',
          businessId: '2',
          isBlocked: false,
          createdAt: new Date().toISOString() 
        }
      ],
      inventory: [
        { 
          id: '1', 
          name: 'Nike Air Max', 
          brand: 'Nike', 
          sizes: { '38': 5, '39': 3, '40': 8, '41': 2 }, 
          purchasePrice: 80, 
          salePrice: 150, 
          ownerId: '2',
          businessId: '2',
          createdAt: new Date().toISOString() 
        }
      ],
      sales: [
        { 
          id: '1', 
          date: new Date().toISOString(), 
          productId: '1', 
          productName: 'Nike Air Max', 
          size: '40', 
          quantity: 1, 
          salePrice: 150, 
          sellerId: '3', 
          ownerId: '2',
          businessId: '2'
        }
      ],
      expenses: [
        { 
          id: '1', 
          date: new Date().toISOString(), 
          description: 'Alquiler Local', 
          amount: 500, 
          ownerId: '2',
          businessId: '2'
        }
      ]
    };
  }

  // Inicializar Firebase
  async initialize() {
    console.log('Firebase inicializado (modo demo)');
    return true;
  }

  // Autenticación
  async signIn(email, password) {
    const user = this.localData.users.find(u => u.email === email && u.password === password);
    if (user) {
      if (user.isBlocked) {
        throw new Error('Usuario bloqueado. Contacte al administrador.');
      }
      localStorage.setItem('currentUser', JSON.stringify(user));
      return { user };
    }
    throw new Error('Credenciales incorrectas');
  }

  async signOut() {
    localStorage.removeItem('currentUser');
    return true;
  }

  getCurrentUser() {
    const stored = localStorage.getItem('currentUser');
    return stored ? JSON.parse(stored) : null;
  }

  // Firestore - Operaciones CRUD
  async getCollection(collectionName, filters = {}) {
    let data = this.localData[collectionName] || [];
    
    // Aplicar filtros
    if (filters.ownerId) {
      data = data.filter(item => item.ownerId === filters.ownerId);
    }
    if (filters.businessId) {
      data = data.filter(item => item.businessId === filters.businessId);
    }
    
    return data;
  }

  async addDocument(collectionName, data) {
    const newDoc = {
      ...data,
      id: Date.now().toString(),
      createdAt: new Date().toISOString(),
      updatedAt: new Date().toISOString()
    };
    
    if (!this.localData[collectionName]) {
      this.localData[collectionName] = [];
    }
    this.localData[collectionName].push(newDoc);
    this.notifyListeners(collectionName);
    return newDoc.id;
  }

  async updateDocument(collectionName, docId, data) {
    const index = this.localData[collectionName].findIndex(item => item.id === docId);
    if (index !== -1) {
      this.localData[collectionName][index] = {
        ...this.localData[collectionName][index],
        ...data,
        updatedAt: new Date().toISOString()
      };
      this.notifyListeners(collectionName);
    }
  }

  async deleteDocument(collectionName, docId) {
    this.localData[collectionName] = this.localData[collectionName].filter(item => item.id !== docId);
    this.notifyListeners(collectionName);
  }

  // Listeners para cambios en tiempo real
  onCollectionChange(collectionName, callback) {
    const listener = { collectionName, callback };
    this.listeners.push(listener);
    
    // Llamar inmediatamente con datos actuales
    callback(this.localData[collectionName] || []);
    
    // Retornar función de limpieza
    return () => {
      this.listeners = this.listeners.filter(l => l !== listener);
    };
  }

  notifyListeners(collectionName) {
    this.listeners
      .filter(l => l.collectionName === collectionName)
      .forEach(l => l.callback(this.localData[collectionName] || []));
  }

  // Estado de conexión
  setOnlineStatus(status) {
    this.isOnline = status;
  }

  getOnlineStatus() {
    return this.isOnline;
  }
}

// Instancia global del servicio
const firebaseService = new FirebaseService();

// ============================================
// COMPONENTE PRINCIPAL
// ============================================
export default function AmeliaContableApp() {
  const [currentUser, setCurrentUser] = useState(null);
  const [activeSection, setActiveSection] = useState('dashboard');
  const [users, setUsers] = useState([]);
  const [inventory, setInventory] = useState([]);
  const [sales, setSales] = useState([]);
  const [expenses, setExpenses] = useState([]);
  const [showMenu, setShowMenu] = useState(false);
  const [notification, setNotification] = useState(null);
  const [isOnline, setIsOnline] = useState(true);
  const [isLoading, setIsLoading] = useState(true);
  const [isSyncing, setIsSyncing] = useState(false);

  // Inicializar Firebase y cargar datos
  useEffect(() => {
    const initializeApp = async () => {
      try {
        await firebaseService.initialize();
        
        // Verificar usuario autenticado
        const user = firebaseService.getCurrentUser();
        if (user) {
          setCurrentUser(user);
        }
        
        // Verificar conexión
        const checkOnlineStatus = () => {
          setIsOnline(navigator.onLine);
          firebaseService.setOnlineStatus(navigator.onLine);
        };
        
        window.addEventListener('online', checkOnlineStatus);
        window.addEventListener('offline', checkOnlineStatus);
        checkOnlineStatus();
        
        setIsLoading(false);
        
        return () => {
          window.removeEventListener('online', checkOnlineStatus);
          window.removeEventListener('offline', checkOnlineStatus);
        };
      } catch (error) {
        console.error('Error inicializando Firebase:', error);
        setIsLoading(false);
      }
    };
    
    initializeApp();
  }, []);

  // Suscribirse a cambios en tiempo real
  useEffect(() => {
    if (!currentUser) return;
    
    const unsubscribers = [];
    
    // Determinar filtros según el rol
    const filters = {};
    if (currentUser.role === 'owner') {
      filters.businessId = currentUser.id;
    } else if (currentUser.role === 'seller') {
      filters.businessId = currentUser.businessId;
    }
    
    // Suscribirse a usuarios
    if (currentUser.role !== 'seller') {
      const unsubUsers = firebaseService.onCollectionChange('users', (data) => {
        if (currentUser.role === 'superadmin') {
          setUsers(data);
        } else {
          // Los dueños solo ven sus vendedores
          setUsers(data.filter(u => u.ownerId === currentUser.id || u.id === currentUser.id));
        }
      });
      unsubscribers.push(unsubUsers);
    }
    
    // Suscribirse a inventario
    if (currentUser.role !== 'seller') {
      const unsubInventory = firebaseService.onCollectionChange('inventory', (data) => {
        if (currentUser.role === 'superadmin') {
          setInventory(data);
        } else {
          setInventory(data.filter(item => item.businessId === currentUser.id));
        }
      });
      unsubscribers.push(unsubInventory);
    } else {
      // Los vendedores necesitan ver el inventario para vender
      const unsubInventory = firebaseService.onCollectionChange('inventory', (data) => {
        setInventory(data.filter(item => item.businessId === currentUser.businessId));
      });
      unsubscribers.push(unsubInventory);
    }
    
    // Suscribirse a ventas
    const unsubSales = firebaseService.onCollectionChange('sales', (data) => {
      if (currentUser.role === 'superadmin') {
        setSales(data);
      } else if (currentUser.role === 'owner') {
        setSales(data.filter(sale => sale.businessId === currentUser.id));
      } else {
        setSales(data.filter(sale => sale.sellerId === currentUser.id));
      }
    });
    unsubscribers.push(unsubSales);
    
    // Suscribirse a gastos
    if (currentUser.role !== 'seller') {
      const unsubExpenses = firebaseService.onCollectionChange('expenses', (data) => {
        if (currentUser.role === 'superadmin') {
          setExpenses(data);
        } else {
          setExpenses(data.filter(expense => expense.businessId === currentUser.id));
        }
      });
      unsubscribers.push(unsubExpenses);
    }
    
    // Limpiar suscripciones al desmontar
    return () => {
      unsubscribers.forEach(unsub => unsub());
    };
  }, [currentUser]);

  // Función para mostrar notificaciones
  const showNotification = (message, type = 'success') => {
    setNotification({ message, type });
    setTimeout(() => setNotification(null), 3000);
  };

  // Función para sincronizar datos
  const syncData = async () => {
    setIsSyncing(true);
    showNotification('Sincronizando datos...');
    
    // Aquí simularemos la sincronización
    setTimeout(() => {
      setIsSyncing(false);
      showNotification('Datos sincronizados correctamente');
    }, 2000);
  };

  // Funciones de cálculo
  const calculateStockValue = () => {
    return inventory.reduce((total, item) => {
      const totalUnits = Object.values(item.sizes || {}).reduce((sum, qty) => sum + qty, 0);
      return total + (totalUnits * item.purchasePrice);
    }, 0);
  };

  const calculateRevenue = (period = 'all') => {
    const now = new Date();
    const filteredSales = sales.filter(sale => {
      if (!sale.date) return false;
      const saleDate = new Date(sale.date);
      
      if (period === 'daily') {
        return saleDate.toDateString() === now.toDateString();
      } else if (period === 'monthly') {
        return saleDate.getMonth() === now.getMonth() && saleDate.getFullYear() === now.getFullYear();
      }
      return true;
    });
    
    return filteredSales.reduce((total, sale) => total + (sale.salePrice * sale.quantity), 0);
  };

  const calculateExpenses = (period = 'all') => {
    const now = new Date();
    const filteredExpenses = expenses.filter(expense => {
      if (!expense.date) return false;
      const expenseDate = new Date(expense.date);
      
      if (period === 'daily') {
        return expenseDate.toDateString() === now.toDateString();
      } else if (period === 'monthly') {
        return expenseDate.getMonth() === now.getMonth() && expenseDate.getFullYear() === now.getFullYear();
      }
      return true;
    });
    
    return filteredExpenses.reduce((total, expense) => total + expense.amount, 0);
  };

  const calculateProfit = (period = 'all') => {
    const revenue = calculateRevenue(period);
    const totalExpenses = calculateExpenses(period);
    const now = new Date();
    
    const filteredSales = sales.filter(sale => {
      if (!sale.date) return false;
      const saleDate = new Date(sale.date);
      
      if (period === 'daily') {
        return saleDate.toDateString() === now.toDateString();
      } else if (period === 'monthly') {
        return saleDate.getMonth() === now.getMonth() && saleDate.getFullYear() === now.getFullYear();
      }
      return true;
    });
    
    const costOfGoods = filteredSales.reduce((total, sale) => {
      const product = inventory.find(p => p.id === sale.productId);
      return total + ((product?.purchasePrice || 0) * sale.quantity);
    }, 0);
    
    return revenue - costOfGoods - totalExpenses;
  };

  const appValue = {
    currentUser,
    setCurrentUser,
    users,
    setUsers,
    inventory,
    setInventory,
    sales,
    setSales,
    expenses,
    setExpenses,
    showNotification,
    calculateStockValue,
    calculateRevenue,
    calculateExpenses,
    calculateProfit,
    firebaseService,
    isOnline,
    syncData,
    isSyncing
  };

  if (isLoading) {
    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center">
        <div className="text-center text-white">
          <div className="text-6xl mb-4">📊</div>
          <p className="text-xl">Cargando Amelia Contable...</p>
        </div>
      </div>
    );
  }

  if (!currentUser) {
    return (
      <AppContext.Provider value={appValue}>
        <LoginScreen />
      </AppContext.Provider>
    );
  }

  return (
    <AppContext.Provider value={appValue}>
      <div className="min-h-screen bg-gray-50">
        {/* Notificación */}
        {notification && (
          <div className={`fixed top-4 right-4 z-50 p-4 rounded-lg shadow-lg flex items-center gap-2 ${
            notification.type === 'success' ? 'bg-green-500' : 'bg-red-500'
          } text-white`}>
            {notification.type === 'success' ? <Check size={20} /> : <AlertCircle size={20} />}
            {notification.message}
          </div>
        )}

        {/* Indicador de conexión */}
        <div className={`fixed bottom-4 left-4 z-50 p-2 rounded-lg shadow-lg flex items-center gap-2 ${
          isOnline ? 'bg-green-500' : 'bg-red-500'
        } text-white text-sm`}>
          {isOnline ? <Wifi size={16} /> : <WifiOff size={16} />}
          {isOnline ? 'En línea' : 'Sin conexión'}
        </div>

        {/* Header */}
        <header className="bg-blue-600 text-white p-4 shadow-lg">
          <div className="flex justify-between items-center">
            <div className="flex items-center gap-3">
              <button onClick={() => setShowMenu(!showMenu)} className="lg:hidden">
                {showMenu ? <X size={24} /> : <Menu size={24} />}
              </button>
              <div className="flex items-center gap-2">
                <span className="text-2xl">📊</span>
                <h1 className="text-xl font-bold">Amelia Contable</h1>
              </div>
            </div>
            <div className="flex items-center gap-3">
              {isSyncing && (
                <RefreshCw className="animate-spin" size={20} />
              )}
              <button
                onClick={syncData}
                className="p-2 hover:bg-blue-700 rounded"
                title="Sincronizar datos"
              >
                <RefreshCw size={20} />
              </button>
              <div className="flex flex-col items-end">
                <span className="text-sm font-medium">{currentUser.name}</span>
                {currentUser.businessName && (
                  <span className="text-xs opacity-75">{currentUser.businessName}</span>
                )}
              </div>
              <span className="text-xs bg-blue-500 px-2 py-1 rounded">
                {currentUser.role === 'superadmin' ? 'Admin' : currentUser.role === 'owner' ? 'Dueño' : 'Vendedor'}
              </span>
              <button
                onClick={async () => {
                  await firebaseService.signOut();
                  setCurrentUser(null);
                  showNotification('Sesión cerrada correctamente');
                }}
                className="p-2 hover:bg-blue-700 rounded"
              >
                <LogOut size={20} />
              </button>
            </div>
          </div>
        </header>

        <div className="flex">
          {/* Sidebar */}
          <aside className={`${showMenu ? 'block' : 'hidden'} lg:block w-64 bg-white shadow-lg min-h-screen`}>
            <Navigation activeSection={activeSection} setActiveSection={setActiveSection} />
          </aside>

          {/* Main Content */}
          <main className="flex-1 p-6">
            <Dashboard activeSection={activeSection} />
          </main>
        </div>
      </div>
    </AppContext.Provider>
  );
}

// ============================================
// COMPONENTE DE LOGIN
// ============================================
function LoginScreen() {
  const { firebaseService, setCurrentUser, showNotification } = useApp();
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [error, setError] = useState('');
  const [isLoading, setIsLoading] = useState(false);

  const handleLogin = async () => {
    if (!email || !password) {
      setError('Por favor ingrese email y contraseña');
      setTimeout(() => setError(''), 3000);
      return;
    }
    
    setIsLoading(true);
    try {
      const result = await firebaseService.signIn(email, password);
      setCurrentUser(result.user);
      showNotification(`Bienvenido ${result.user.name}`);
    } catch (error) {
      setError(error.message);
      setTimeout(() => setError(''), 3000);
    } finally {
      setIsLoading(false);
    }
  };

  const handleKeyPress = (e) => {
    if (e.key === 'Enter') {
      handleLogin();
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center p-4">
      <div className="bg-white rounded-lg shadow-xl p-8 w-full max-w-md">
        <div className="text-center mb-8">
          <div className="text-6xl mb-3">📊</div>
          <h2 className="text-2xl font-bold text-gray-800">Amelia Contable</h2>
          <p className="text-gray-600 mt-2">Sistema de Gestión para Zapaterías</p>
        </div>
        
        {error && (
          <div className="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded mb-4">
            {error}
          </div>
        )}
        
        <div className="space-y-4">
          <div>
            <label className="block text-sm font-medium text-gray-700 mb-2">Email</label>
            <input
              type="email"
              value={email}
              onChange={(e) => setEmail(e.target.value)}
              onKeyPress={handleKeyPress}
              className="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
              placeholder="correo@ejemplo.com"
              disabled={isLoading}
            />
          </div>
          
          <div>
            <label className="block text-sm font-medium text-gray-700 mb-2">Contraseña</label>
            <input
              type="password"
              value={password}
              onChange={(e) => setPassword(e.target.value)}
              onKeyPress={handleKeyPress}
              className="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
              placeholder="••••••••"
              disabled={isLoading}
            />
          </div>
          
          <button
            onClick={handleLogin}
            disabled={isLoading}
            className="w-full bg-blue-600 text-white py-2 px-4 rounded-lg hover:bg-blue-700 transition duration-200 disabled:opacity-50"
          >
            {isLoading ? 'Iniciando sesión...' : 'Iniciar Sesión'}
          </button>
          
          <div className="mt-4 p-3 bg-yellow-50 border border-yellow-200 rounded-lg">
            <p className="text-xs text-yellow-800">
              <strong>Nota:</strong> Para usar con Firebase real, configura tus credenciales en el código.
            </p>
          </div>
        </div>
      </div>
    </div>
  );
}

// ============================================
// COMPONENTE DE NAVEGACIÓN
// ============================================
function Navigation({ activeSection, setActiveSection }) {
  const { currentUser } = useApp();

  const menuItems = [
    { id: 'dashboard', label: 'Dashboard', icon: TrendingUp, roles: ['superadmin', 'owner'] },
    { id: 'inventory', label: 'Inventario', icon: Package, roles: ['superadmin', 'owner'] },
    { id: 'sales', label: 'Ventas', icon: ShoppingCart, roles: ['superadmin', 'owner', 'seller'] },
    { id: 'expenses', label: 'Gastos', icon: DollarSign, roles: ['superadmin', 'owner'] },
    { id: 'users', label: 'Usuarios', icon: Users, roles: ['superadmin', 'owner'] },
    { id: 'reports', label: 'Reportes', icon: FileText, roles: ['superadmin', 'owner'] }
  ];

  return (
    <nav className="p-4">
      {currentUser.businessName && (
        <div className="mb-4 p-3 bg-blue-50 rounded-lg">
          <div className="flex items-center gap-2 text-blue-700">
            <Building size={16} />
            <span className="text-sm font-medium">{currentUser.businessName}</span>
          </div>
        </div>
      )}
      
      {menuItems
        .filter(item => item.roles.includes(currentUser.role))
        .map(item => {
          const Icon = item.icon;
          return (
            <button
              key={item.id}
              onClick={() => setActiveSection(item.id)}
              className={`w-full flex items-center gap-3 p-3 rounded-lg mb-2 transition ${
                activeSection === item.id
                  ? 'bg-blue-100 text-blue-600'
                  : 'hover:bg-gray-100 text-gray-700'
              }`}
            >
              <Icon size={20} />
              <span>{item.label}</span>
            </button>
          );
        })}
    </nav>
  );
}

// ============================================
// DASHBOARD PRINCIPAL
// ============================================
function Dashboard({ activeSection }) {
  const { currentUser } = useApp();

  // Vendedores solo ven ventas
  if (currentUser.role === 'seller') {
    return <SalesSection />;
  }

  switch (activeSection) {
    case 'inventory':
      return <InventorySection />;
    case 'sales':
      return <SalesSection />;
    case 'expenses':
      return <ExpensesSection />;
    case 'users':
      return <UsersSection />;
    case 'reports':
      return <ReportsSection />;
    default:
      return <DashboardOverview />;
  }
}

// ============================================
// VISTA GENERAL DEL DASHBOARD
// ============================================
function DashboardOverview() {
  const { calculateStockValue, calculateRevenue, calculateExpenses, calculateProfit, syncData, isSyncing, currentUser, users, sales, inventory } = useApp();

  const stats = [
    { label: 'Valor del Inventario', value: `$${calculateStockValue().toFixed(2)}`, icon: Package, color: 'bg-blue-500' },
    { label: 'Ventas del Mes', value: `$${calculateRevenue('monthly').toFixed(2)}`, icon: ShoppingCart, color: 'bg-green-500' },
    { label: 'Gastos del Mes', value: `$${calculateExpenses('monthly').toFixed(2)}`, icon: DollarSign, color: 'bg-red-500' },
    { label: 'Ganancia del Mes', value: `$${calculateProfit('monthly').toFixed(2)}`, icon: TrendingUp, color: 'bg-purple-500' }
  ];

  // Estadísticas adicionales para superadmin
  const businessStats = currentUser.role === 'superadmin' ? {
    totalBusinesses: users.filter(u => u.role === 'owner').length,
    totalSellers: users.filter(u => u.role === 'seller').length,
    totalProducts: inventory.length,
    totalSales: sales.length
  } : null;

  return (
    <div>
      <div className="flex justify-between items-center mb-6">
        <div>
          <h2 className="text-2xl font-bold">Dashboard</h2>
          {currentUser.businessName && (
            <p className="text-gray-600 text-sm mt-1">{currentUser.businessName}</p>
          )}
        </div>
        <button
          onClick={syncData}
          disabled={isSyncing}
          className="flex items-center gap-2 bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 disabled:opacity-50"
        >
          <RefreshCw className={isSyncing ? 'animate-spin' : ''} size={20} />
          {isSyncing ? 'Sincronizando...' : 'Sincronizar'}
        </button>
      </div>
      
      {currentUser.role === 'superadmin' && businessStats && (
        <div className="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
          <div className="bg-white rounded-lg shadow p-4">
            <div className="flex items-center gap-3">
              <Building className="text-blue-600" size={24} />
              <div>
                <p className="text-2xl font-bold">{businessStats.totalBusinesses}</p>
                <p className="text-sm text-gray-600">Negocios</p>
              </div>
            </div>
          </div>
          <div className="bg-white rounded-lg shadow p-4">
            <div className="flex items-center gap-3">
              <Users className="text-green-600" size={24} />
              <div>
                <p className="text-2xl font-bold">{businessStats.totalSellers}</p>
                <p className="text-sm text-gray-600">Vendedores</p>
              </div>
            </div>
          </div>
          <div className="bg-white rounded-lg shadow p-4">
            <div className="flex items-center gap-3">
              <Package className="text-purple-600" size={24} />
              <div>
                <p className="text-2xl font-bold">{businessStats.totalProducts}</p>
                <p className="text-sm text-gray-600">Productos</p>
              </div>
            </div>
          </div>
          <div className="bg-white rounded-lg shadow p-4">
            <div className="flex items-center gap-3">
              <ShoppingCart className="text-orange-600" size={24} />
              <div>
                <p className="text-2xl font-bold">{businessStats.totalSales}</p>
                <p className="text-sm text-gray-600">Ventas Totales</p>
              </div>
            </div>
          </div>
        </div>
      )}
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
        {stats.map((stat, index) => {
          const Icon = stat.icon;
          return (
            <div key={index} className="bg-white rounded-lg shadow p-6">
              <div className="flex items-center justify-between mb-4">
                <div className={`${stat.color} text-white p-3 rounded-lg`}>
                  <Icon size={24} />
                </div>
              </div>
              <p className="text-gray-600 text-sm">{stat.label}</p>
              <p className="text-2xl font-bold text-gray-800">{stat.value}</p>
            </div>
          );
        })}
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4">Resumen Diario</h3>
          <div className="space-y-3">
            <div className="flex justify-between">
              <span className="text-gray-600">Ventas de Hoy</span>
              <span className="font-semibold">${calculateRevenue('daily').toFixed(2)}</span>
            </div>
            <div className="flex justify-between">
              <span className="text-gray-600">Gastos de Hoy</span>
              <span className="font-semibold">${calculateExpenses('daily').toFixed(2)}</span>
            </div>
            <div className="border-t pt-3 flex justify-between">
              <span className="text-gray-600">Ganancia de Hoy</span>
              <span className="font-bold text-green-600">${calculateProfit('daily').toFixed(2)}</span>
            </div>
          </div>
        </div>

        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4">Balance General</h3>
          <div className="space-y-3">
            <div className="flex justify-between">
              <span className="text-gray-600">Total Ventas</span>
              <span className="font-semibold">${calculateRevenue('all').toFixed(2)}</span>
            </div>
            <div className="flex justify-between">
              <span className="text-gray-600">Total Gastos</span>
              <span className="font-semibold">${calculateExpenses('all').toFixed(2)}</span>
            </div>
            <div className="border-t pt-3 flex justify-between">
              <span className="text-gray-600">Ganancia Total</span>
              <span className="font-bold text-green-600">${calculateProfit('all').toFixed(2)}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}

// ============================================
// SECCIÓN DE INVENTARIO
// ============================================
function InventorySection() {
  const { inventory, firebaseService, currentUser, showNotification } = useApp();
  const [showAddForm, setShowAddForm] = useState(false);
  const [editingItem, setEditingItem] = useState(null);
  const [formData, setFormData] = useState({
    name: '',
    brand: '',
    sizes: {},
    purchasePrice: '',
    salePrice: ''
  });
  const [sizeInput, setSizeInput] = useState({ size: '', quantity: '' });
  const [isSubmitting, setIsSubmitting] = useState(false);

  const handleAddProduct = async () => {
    if (!formData.name || !formData.purchasePrice || !formData.salePrice) {
      showNotification('Por favor complete todos los campos', 'error');
      return;
    }

    setIsSubmitting(true);
    try {
      const productData = {
        ...formData,
        purchasePrice: parseFloat(formData.purchasePrice),
        salePrice: parseFloat(formData.salePrice),
        ownerId: currentUser.role === 'owner' ? currentUser.id : null,
        businessId: currentUser.role === 'owner' ? currentUser.id : null
      };

      if (editingItem) {
        await firebaseService.updateDocument('inventory', editingItem.id, productData);
        showNotification('Producto actualizado correctamente');
      } else {
        await firebaseService.addDocument('inventory', productData);
        showNotification('Producto agregado correctamente');
      }

      setFormData({ name: '', brand: '', sizes: {}, purchasePrice: '', salePrice: '' });
      setShowAddForm(false);
      setEditingItem(null);
    } catch (error) {
      showNotification('Error al guardar el producto', 'error');
    } finally {
      setIsSubmitting(false);
    }
  };

  const handleAddSize = () => {
    if (sizeInput.size && sizeInput.quantity) {
      setFormData({
        ...formData,
        sizes: {
          ...formData.sizes,
          [sizeInput.size]: parseInt(sizeInput.quantity)
        }
      });
      setSizeInput({ size: '', quantity: '' });
    }
  };

  const handleDeleteProduct = async (id) => {
    try {
      await firebaseService.deleteDocument('inventory', id);
      showNotification('Producto eliminado');
    } catch (error) {
      showNotification('Error al eliminar el producto', 'error');
    }
  };

  const handleEditProduct = (item) => {
    setFormData({
      name: item.name,
      brand: item.brand,
      sizes: item.sizes || {},
      purchasePrice: item.purchasePrice.toString(),
      salePrice: item.salePrice.toString()
    });
    setEditingItem(item);
    setShowAddForm(true);
  };

  return (
    <div>
      <div className="flex justify-between items-center mb-6">
        <h2 className="text-2xl font-bold">Inventario</h2>
        <button
          onClick={() => setShowAddForm(true)}
          className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 flex items-center gap-2"
        >
          <Plus size={20} />
          Agregar Producto
        </button>
      </div>

      {showAddForm && (
        <div className="bg-white rounded-lg shadow p-6 mb-6">
          <h3 className="text-lg font-semibold mb-4">
            {editingItem ? 'Editar Producto' : 'Nuevo Producto'}
          </h3>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <input
              type="text"
              placeholder="Nombre del producto"
              value={formData.name}
              onChange={(e) => setFormData({ ...formData, name: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="text"
              placeholder="Marca"
              value={formData.brand}
              onChange={(e) => setFormData({ ...formData, brand: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="number"
              placeholder="Precio de compra"
              value={formData.purchasePrice}
              onChange={(e) => setFormData({ ...formData, purchasePrice: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="number"
              placeholder="Precio de venta"
              value={formData.salePrice}
              onChange={(e) => setFormData({ ...formData, salePrice: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
          </div>

          <div className="mt-4">
            <h4 className="font-medium mb-2">Tallas y Cantidades</h4>
            <div className="flex gap-2 mb-2">
              <input
                type="text"
                placeholder="Talla"
                value={sizeInput.size}
                onChange={(e) => setSizeInput({ ...sizeInput, size: e.target.value })}
                className="px-4 py-2 border rounded-lg flex-1"
                disabled={isSubmitting}
              />
              <input
                type="number"
                placeholder="Cantidad"
                value={sizeInput.quantity}
                onChange={(e) => setSizeInput({ ...sizeInput, quantity: e.target.value })}
                className="px-4 py-2 border rounded-lg flex-1"
                disabled={isSubmitting}
              />
              <button
                onClick={handleAddSize}
                disabled={isSubmitting}
                className="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 disabled:opacity-50"
              >
                Agregar Talla
              </button>
            </div>
            <div className="flex flex-wrap gap-2">
              {Object.entries(formData.sizes).map(([size, qty]) => (
                <span key={size} className="bg-gray-100 px-3 py-1 rounded-full text-sm">
                  Talla {size}: {qty} unidades
                  <button
                    onClick={() => {
                      const newSizes = { ...formData.sizes };
                      delete newSizes[size];
                      setFormData({ ...formData, sizes: newSizes });
                    }}
                    className="ml-2 text-red-500 hover:text-red-700"
                    disabled={isSubmitting}
                  >
                    ×
                  </button>
                </span>
              ))}
            </div>
          </div>

          <div className="flex gap-2 mt-4">
            <button
              onClick={handleAddProduct}
              disabled={isSubmitting}
              className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 flex items-center gap-2 disabled:opacity-50"
            >
              <Save size={20} />
              {isSubmitting ? 'Guardando...' : (editingItem ? 'Actualizar' : 'Guardar')}
            </button>
            <button
              onClick={() => {
                setShowAddForm(false);
                setEditingItem(null);
                setFormData({ name: '', brand: '', sizes: {}, purchasePrice: '', salePrice: '' });
              }}
              disabled={isSubmitting}
              className="bg-gray-300 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-400 disabled:opacity-50"
            >
              Cancelar
            </button>
          </div>
        </div>
      )}

      <div className="bg-white rounded-lg shadow overflow-hidden">
        <table className="w-full">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Producto
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Marca
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Stock
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                P. Compra
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                P. Venta
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Valor Stock
              </th>
              {currentUser.role === 'superadmin' && (
                <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Negocio
                </th>
              )}
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Acciones
              </th>
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {inventory.map(item => {
              const totalStock = Object.values(item.sizes || {}).reduce((sum, qty) => sum + qty, 0);
              const stockValue = totalStock * item.purchasePrice;
              
              return (
                <tr key={item.id}>
                  <td className="px-6 py-4 whitespace-nowrap">
                    <div className="text-sm font-medium text-gray-900">{item.name}</div>
                    <div className="text-xs text-gray-500">
                      {Object.entries(item.sizes || {}).map(([size, qty]) => 
                        `T${size}: ${qty}`
                      ).join(' | ')}
                    </div>
                  </td>
                  <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                    {item.brand}
                  </td>
                  <td className="px-6 py-4 whitespace-nowrap">
                    <span className={`px-2 py-1 text-xs rounded-full ${
                      totalStock > 10 ? 'bg-green-100 text-green-800' : 
                      totalStock > 5 ? 'bg-yellow-100 text-yellow-800' : 
                      'bg-red-100 text-red-800'
                    }`}>
                      {totalStock} unidades
                    </span>
                  </td>
                  <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                    ${item.purchasePrice}
                  </td>
                  <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                    ${item.salePrice}
                  </td>
                  <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                    ${stockValue.toFixed(2)}
                  </td>
                  {currentUser.role === 'superadmin' && (
                    <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                      {item.businessId || '-'}
                    </td>
                  )}
                  <td className="px-6 py-4 whitespace-nowrap text-sm font-medium">
                    <button
                      onClick={() => handleEditProduct(item)}
                      className="text-blue-600 hover:text-blue-900 mr-3"
                    >
                      <Edit size={18} />
                    </button>
                    <button
                      onClick={() => handleDeleteProduct(item.id)}
                      className="text-red-600 hover:text-red-900"
                    >
                      <Trash2 size={18} />
                    </button>
                  </td>
                </tr>
              );
            })}
          </tbody>
        </table>
      </div>
    </div>
  );
}

// ============================================
// SECCIÓN DE VENTAS
// ============================================
function SalesSection() {
  const { inventory, sales, firebaseService, currentUser, showNotification } = useApp();
  const [showSaleForm, setShowSaleForm] = useState(false);
  const [selectedProduct, setSelectedProduct] = useState('');
  const [selectedSize, setSelectedSize] = useState('');
  const [quantity, setQuantity] = useState(1);
  const [customPrice, setCustomPrice] = useState('');
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [editingSale, setEditingSale] = useState(null);

  const handleSale = async () => {
    if (!selectedProduct || !selectedSize || !quantity) {
      showNotification('Por favor complete todos los campos', 'error');
      return;
    }

    const product = inventory.find(p => p.id === selectedProduct);
    if (!product) return;

    if (!editingSale && (product.sizes[selectedSize] || 0) < quantity) {
      showNotification('Stock insuficiente', 'error');
      return;
    }

    setIsSubmitting(true);
    try {
      const salePrice = customPrice ? parseFloat(customPrice) : product.salePrice;

      const saleData = {
        date: new Date().toISOString(),
        productId: selectedProduct,
        productName: product.name,
        size: selectedSize,
        quantity: parseInt(quantity),
        salePrice,
        sellerId: currentUser.id,
        ownerId: currentUser.role === 'owner' ? currentUser.id : currentUser.ownerId,
        businessId: currentUser.role === 'owner' ? currentUser.id : currentUser.businessId
      };

      if (editingSale) {
        await firebaseService.updateDocument('sales', editingSale.id, saleData);
        showNotification('Venta actualizada correctamente');
      } else {
        await firebaseService.addDocument('sales', saleData);

        // Actualizar inventario
        const updatedSizes = {
          ...product.sizes,
          [selectedSize]: product.sizes[selectedSize] - parseInt(quantity)
        };
        
        await firebaseService.updateDocument('inventory', selectedProduct, { sizes: updatedSizes });
        showNotification('Venta registrada correctamente');
      }
      
      setSelectedProduct('');
      setSelectedSize('');
      setQuantity(1);
      setCustomPrice('');
      setShowSaleForm(false);
      setEditingSale(null);
    } catch (error) {
      showNotification('Error al procesar la venta', 'error');
    } finally {
      setIsSubmitting(false);
    }
  };

  const handleEditSale = (sale) => {
    setEditingSale(sale);
    setSelectedProduct(sale.productId);
    setSelectedSize(sale.size);
    setQuantity(sale.quantity);
    setCustomPrice(sale.salePrice.toString());
    setShowSaleForm(true);
  };

  const handleDeleteSale = async (sale) => {
    try {
      // Restaurar inventario
      const product = inventory.find(p => p.id === sale.productId);
      if (product) {
        const updatedSizes = {
          ...product.sizes,
          [sale.size]: (product.sizes[sale.size] || 0) + sale.quantity
        };
        await firebaseService.updateDocument('inventory', sale.productId, { sizes: updatedSizes });
      }
      
      await firebaseService.deleteDocument('sales', sale.id);
      showNotification('Venta eliminada correctamente');
    } catch (error) {
      showNotification('Error al eliminar la venta', 'error');
    }
  };

  return (
    <div>
      <div className="flex justify-between items-center mb-6">
        <h2 className="text-2xl font-bold">Ventas</h2>
        <button
          onClick={() => setShowSaleForm(true)}
          className="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 flex items-center gap-2"
        >
          <ShoppingCart size={20} />
          Nueva Venta
        </button>
      </div>

      {showSaleForm && (
        <div className="bg-white rounded-lg shadow p-6 mb-6">
          <h3 className="text-lg font-semibold mb-4">
            {editingSale ? 'Editar Venta' : 'Registrar Venta'}
          </h3>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">Producto</label>
              <select
                value={selectedProduct}
                onChange={(e) => {
                  setSelectedProduct(e.target.value);
                  setSelectedSize('');
                  const product = inventory.find(p => p.id === e.target.value);
                  setCustomPrice(product ? product.salePrice.toString() : '');
                }}
                className="w-full px-4 py-2 border rounded-lg"
                disabled={isSubmitting}
              >
                <option value="">Seleccionar producto</option>
                {inventory.map(product => (
                  <option key={product.id} value={product.id}>
                    {product.name} - {product.brand}
                  </option>
                ))}
              </select>
            </div>

            {selectedProduct && (
              <>
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">Talla</label>
                  <select
                    value={selectedSize}
                    onChange={(e) => setSelectedSize(e.target.value)}
                    className="w-full px-4 py-2 border rounded-lg"
                    disabled={isSubmitting}
                  >
                    <option value="">Seleccionar talla</option>
                    {Object.entries(inventory.find(p => p.id === selectedProduct)?.sizes || {})
                      .filter(([size, qty]) => qty > 0 || editingSale)
                      .map(([size, qty]) => (
                        <option key={size} value={size}>
                          Talla {size} ({qty} disponibles)
                        </option>
                      ))}
                  </select>
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">Cantidad</label>
                  <input
                    type="number"
                    min="1"
                    value={quantity}
                    onChange={(e) => setQuantity(e.target.value)}
                    className="w-full px-4 py-2 border rounded-lg"
                    disabled={isSubmitting}
                  />
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Precio de Venta (modificable)
                  </label>
                  <input
                    type="number"
                    value={customPrice}
                    onChange={(e) => setCustomPrice(e.target.value)}
                    className="w-full px-4 py-2 border rounded-lg"
                    disabled={isSubmitting}
                  />
                </div>
              </>
            )}
          </div>

          {selectedProduct && selectedSize && (
            <div className="mt-4 p-4 bg-gray-50 rounded-lg">
              <p className="text-sm text-gray-600">Resumen de venta:</p>
              <p className="text-lg font-semibold">
                Total: ${((customPrice || 0) * quantity).toFixed(2)}
              </p>
            </div>
          )}

          <div className="flex gap-2 mt-4">
            <button
              onClick={handleSale}
              disabled={isSubmitting}
              className="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 disabled:opacity-50"
            >
              {isSubmitting ? 'Procesando...' : (editingSale ? 'Actualizar Venta' : 'Confirmar Venta')}
            </button>
            <button
              onClick={() => {
                setShowSaleForm(false);
                setSelectedProduct('');
                setSelectedSize('');
                setQuantity(1);
                setCustomPrice('');
                setEditingSale(null);
              }}
              disabled={isSubmitting}
              className="bg-gray-300 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-400 disabled:opacity-50"
            >
              Cancelar
            </button>
          </div>
        </div>
      )}

      <div className="bg-white rounded-lg shadow overflow-hidden">
        <table className="w-full">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Fecha
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Producto
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Talla
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Cantidad
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Precio Unit.
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Total
              </th>
              {currentUser.role === 'superadmin' && (
                <>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Negocio
                  </th>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Acciones
                  </th>
                </>
              )}
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {sales.map(sale => (
              <tr key={sale.id}>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {sale.date ? new Date(sale.date).toLocaleDateString() : '-'}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  {sale.productName}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {sale.size}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {sale.quantity}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  ${sale.salePrice}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                  ${(sale.salePrice * sale.quantity).toFixed(2)}
                </td>
                {currentUser.role === 'superadmin' && (
                  <>
                    <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                      {sale.businessId || '-'}
                    </td>
                    <td className="px-6 py-4 whitespace-nowrap text-sm font-medium">
                      <button
                        onClick={() => handleEditSale(sale)}
                        className="text-blue-600 hover:text-blue-900 mr-3"
                      >
                        <Edit size={18} />
                      </button>
                      <button
                        onClick={() => handleDeleteSale(sale)}
                        className="text-red-600 hover:text-red-900"
                      >
                        <Trash2 size={18} />
                      </button>
                    </td>
                  </>
                )}
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
}

// ============================================
// SECCIÓN DE GASTOS
// ============================================
function ExpensesSection() {
  const { expenses, firebaseService, currentUser, showNotification } = useApp();
  const [showAddForm, setShowAddForm] = useState(false);
  const [description, setDescription] = useState('');
  const [amount, setAmount] = useState('');
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [editingExpense, setEditingExpense] = useState(null);

  const handleAddExpense = async () => {
    if (!description || !amount) {
      showNotification('Por favor complete todos los campos', 'error');
      return;
    }

    setIsSubmitting(true);
    try {
      const expenseData = {
        date: new Date().toISOString(),
        description,
        amount: parseFloat(amount),
        ownerId: currentUser.role === 'owner' ? currentUser.id : null,
        businessId: currentUser.role === 'owner' ? currentUser.id : null
      };

      if (editingExpense) {
        await firebaseService.updateDocument('expenses', editingExpense.id, expenseData);
        showNotification('Gasto actualizado correctamente');
      } else {
        await firebaseService.addDocument('expenses', expenseData);
        showNotification('Gasto registrado correctamente');
      }
      
      setDescription('');
      setAmount('');
      setShowAddForm(false);
      setEditingExpense(null);
    } catch (error) {
      showNotification('Error al guardar el gasto', 'error');
    } finally {
      setIsSubmitting(false);
    }
  };

  const handleEditExpense = (expense) => {
    setEditingExpense(expense);
    setDescription(expense.description);
    setAmount(expense.amount.toString());
    setShowAddForm(true);
  };

  const handleDeleteExpense = async (id) => {
    try {
      await firebaseService.deleteDocument('expenses', id);
      showNotification('Gasto eliminado');
    } catch (error) {
      showNotification('Error al eliminar el gasto', 'error');
    }
  };

  return (
    <div>
      <div className="flex justify-between items-center mb-6">
        <h2 className="text-2xl font-bold">Gastos</h2>
        <button
          onClick={() => setShowAddForm(true)}
          className="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 flex items-center gap-2"
        >
          <Plus size={20} />
          Agregar Gasto
        </button>
      </div>

      {showAddForm && (
        <div className="bg-white rounded-lg shadow p-6 mb-6">
          <h3 className="text-lg font-semibold mb-4">
            {editingExpense ? 'Editar Gasto' : 'Nuevo Gasto'}
          </h3>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <input
              type="text"
              placeholder="Descripción del gasto"
              value={description}
              onChange={(e) => setDescription(e.target.value)}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="number"
              placeholder="Monto"
              value={amount}
              onChange={(e) => setAmount(e.target.value)}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
          </div>

          <div className="flex gap-2 mt-4">
            <button
              onClick={handleAddExpense}
              disabled={isSubmitting}
              className="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 disabled:opacity-50"
            >
              {isSubmitting ? 'Guardando...' : (editingExpense ? 'Actualizar Gasto' : 'Registrar Gasto')}
            </button>
            <button
              onClick={() => {
                setShowAddForm(false);
                setDescription('');
                setAmount('');
                setEditingExpense(null);
              }}
              disabled={isSubmitting}
              className="bg-gray-300 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-400 disabled:opacity-50"
            >
              Cancelar
            </button>
          </div>
        </div>
      )}

      <div className="bg-white rounded-lg shadow overflow-hidden">
        <table className="w-full">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Fecha
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Descripción
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Monto
              </th>
              {currentUser.role === 'superadmin' && (
                <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Negocio
                </th>
              )}
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Acciones
              </th>
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {expenses.map(expense => (
              <tr key={expense.id}>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {expense.date ? new Date(expense.date).toLocaleDateString() : '-'}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  {expense.description}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                  ${expense.amount.toFixed(2)}
                </td>
                {currentUser.role === 'superadmin' && (
                  <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                    {expense.businessId || '-'}
                  </td>
                )}
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium">
                  {(currentUser.role === 'superadmin' || currentUser.role === 'owner') && (
                    <>
                      <button
                        onClick={() => handleEditExpense(expense)}
                        className="text-blue-600 hover:text-blue-900 mr-3"
                      >
                        <Edit size={18} />
                      </button>
                      <button
                        onClick={() => handleDeleteExpense(expense.id)}
                        className="text-red-600 hover:text-red-900"
                      >
                        <Trash2 size={18} />
                      </button>
                    </>
                  )}
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
}

// ============================================
// SECCIÓN DE USUARIOS
// ============================================
function UsersSection() {
  const { users, firebaseService, currentUser, showNotification } = useApp();
  const [showAddForm, setShowAddForm] = useState(false);
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
    role: 'seller',
    businessName: ''
  });
  const [isSubmitting, setIsSubmitting] = useState(false);

  const handleAddUser = async () => {
    if (!formData.name || !formData.email || !formData.password) {
      showNotification('Por favor complete todos los campos', 'error');
      return;
    }

    if (formData.role === 'owner' && !formData.businessName) {
      showNotification('Por favor ingrese el nombre del negocio', 'error');
      return;
    }

    setIsSubmitting(true);
    try {
      const newUser = {
        ...formData,
        isBlocked: false,
        ownerId: currentUser.role === 'owner' ? currentUser.id : null,
        businessId: currentUser.role === 'owner' ? currentUser.id : null,
        businessName: formData.role === 'owner' ? formData.businessName : 
                      currentUser.role === 'owner' ? currentUser.businessName : null
      };

      await firebaseService.addDocument('users', newUser);
      showNotification('Usuario creado correctamente');
      
      setFormData({ name: '', email: '', password: '', role: 'seller', businessName: '' });
      setShowAddForm(false);
    } catch (error) {
      showNotification('Error al crear el usuario', 'error');
    } finally {
      setIsSubmitting(false);
    }
  };

  const handleToggleBlock = async (user) => {
    try {
      await firebaseService.updateDocument('users', user.id, { isBlocked: !user.isBlocked });
      showNotification(user.isBlocked ? 'Usuario desbloqueado' : 'Usuario bloqueado');
    } catch (error) {
      showNotification('Error al actualizar el usuario', 'error');
    }
  };

  const handleDeleteUser = async (id) => {
    if (id === currentUser.id) {
      showNotification('No puedes eliminarte a ti mismo', 'error');
      return;
    }
    
    try {
      await firebaseService.deleteDocument('users', id);
      showNotification('Usuario eliminado');
    } catch (error) {
      showNotification('Error al eliminar el usuario', 'error');
    }
  };

  return (
    <div>
      <div className="flex justify-between items-center mb-6">
        <h2 className="text-2xl font-bold">Usuarios</h2>
        <button
          onClick={() => setShowAddForm(true)}
          className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 flex items-center gap-2"
        >
          <Plus size={20} />
          Agregar Usuario
        </button>
      </div>

      {showAddForm && (
        <div className="bg-white rounded-lg shadow p-6 mb-6">
          <h3 className="text-lg font-semibold mb-4">Nuevo Usuario</h3>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <input
              type="text"
              placeholder="Nombre completo"
              value={formData.name}
              onChange={(e) => setFormData({ ...formData, name: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="email"
              placeholder="Email"
              value={formData.email}
              onChange={(e) => setFormData({ ...formData, email: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <input
              type="password"
              placeholder="Contraseña"
              value={formData.password}
              onChange={(e) => setFormData({ ...formData, password: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            />
            <select
              value={formData.role}
              onChange={(e) => setFormData({ ...formData, role: e.target.value })}
              className="px-4 py-2 border rounded-lg"
              disabled={isSubmitting}
            >
              {currentUser.role === 'superadmin' && (
                <option value="owner">Dueño de Negocio</option>
              )}
              <option value="seller">Vendedor</option>
            </select>
            
            {formData.role === 'owner' && currentUser.role === 'superadmin' && (
              <input
                type="text"
                placeholder="Nombre del Negocio"
                value={formData.businessName}
                onChange={(e) => setFormData({ ...formData, businessName: e.target.value })}
                className="px-4 py-2 border rounded-lg md:col-span-2"
                disabled={isSubmitting}
              />
            )}
          </div>

          <div className="flex gap-2 mt-4">
            <button
              onClick={handleAddUser}
              disabled={isSubmitting}
              className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 disabled:opacity-50"
            >
              {isSubmitting ? 'Creando...' : 'Crear Usuario'}
            </button>
            <button
              onClick={() => {
                setShowAddForm(false);
                setFormData({ name: '', email: '', password: '', role: 'seller', businessName: '' });
              }}
              disabled={isSubmitting}
              className="bg-gray-300 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-400 disabled:opacity-50"
            >
              Cancelar
            </button>
          </div>
        </div>
      )}

      <div className="bg-white rounded-lg shadow overflow-hidden">
        <table className="w-full">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Nombre
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Email
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Rol
              </th>
              {currentUser.role === 'superadmin' && (
                <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Negocio
                </th>
              )}
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Estado
              </th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Acciones
              </th>
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {users.map(user => (
              <tr key={user.id}>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                  {user.name}
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {user.email}
                </td>
                <td className="px-6 py-4 whitespace-nowrap">
                  <span className={`px-2 py-1 text-xs rounded-full ${
                    user.role === 'superadmin' ? 'bg-purple-100 text-purple-800' :
                    user.role === 'owner' ? 'bg-blue-100 text-blue-800' :
                    'bg-green-100 text-green-800'
                  }`}>
                    {user.role === 'superadmin' ? 'Admin' : 
                     user.role === 'owner' ? 'Dueño' : 'Vendedor'}
                  </span>
                </td>
                {currentUser.role === 'superadmin' && (
                  <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                    {user.businessName || '-'}
                  </td>
                )}
                <td className="px-6 py-4 whitespace-nowrap">
                  <span className={`flex items-center gap-1 text-xs ${
                    user.isBlocked ? 'text-red-600' : 'text-green-600'
                  }`}>
                    {user.isBlocked ? <Lock size={14} /> : <Unlock size={14} />}
                    {user.isBlocked ? 'Bloqueado' : 'Activo'}
                  </span>
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium">
                  {user.id !== currentUser.id && (
                    <>
                      {currentUser.role === 'superadmin' && (
                        <button
                          onClick={() => handleToggleBlock(user)}
                          className={`mr-3 ${
                            user.isBlocked ? 'text-green-600 hover:text-green-900' : 'text-yellow-600 hover:text-yellow-900'
                          }`}
                          title={user.isBlocked ? 'Desbloquear' : 'Bloquear'}
                        >
                          {user.isBlocked ? <Unlock size={18} /> : <Lock size={18} />}
                        </button>
                      )}
                      <button
                        onClick={() => handleDeleteUser(user.id)}
                        className="text-red-600 hover:text-red-900"
                      >
                        <Trash2 size={18} />
                      </button>
                    </>
                  )}
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
}

// ============================================
// SECCIÓN DE REPORTES
// ============================================
function ReportsSection() {
  const { calculateRevenue, calculateExpenses, calculateProfit, sales, inventory, currentUser } = useApp();

  const reportData = {
    daily: {
      revenue: calculateRevenue('daily'),
      expenses: calculateExpenses('daily'),
      profit: calculateProfit('daily')
    },
    monthly: {
      revenue: calculateRevenue('monthly'),
      expenses: calculateExpenses('monthly'),
      profit: calculateProfit('monthly')
    },
    total: {
      revenue: calculateRevenue('all'),
      expenses: calculateExpenses('all'),
      profit: calculateProfit('all')
    }
  };

  return (
    <div>
      <h2 className="text-2xl font-bold mb-6">
        Reportes Completos
        {currentUser.businessName && (
          <span className="text-lg font-normal text-gray-600 ml-2">- {currentUser.businessName}</span>
        )}
      </h2>

      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-6">
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4 text-blue-600">Reporte Diario</h3>
          <div className="space-y-3">
            <div className="flex justify-between">
              <span className="text-gray-600">Ventas</span>
              <span className="font-semibold">${reportData.daily.revenue.toFixed(2)}</span>
            </div>
            <div className="flex justify-between">
              <span className="text-gray-600">Gastos</span>
              <span className="font-semibold text-red-600">-${reportData.daily.expenses.toFixed(2)}</span>
            </div>
            <div className="border-t pt-3 flex justify-between">
              <span className="text-gray-600 font-semibold">Ganancia</span>
              <span className={`font-bold ${reportData.daily.profit >= 0 ? 'text-green-600' : 'text-red-600'}`}>
                ${reportData.daily.profit.toFixed(2)}
              </span>
            </div>
          </div>
        </div>

        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4 text-purple-600">Reporte Mensual</h3>
          <div className="space-y-3">
            <div className="flex justify-between">
              <span className="text-gray-600">Ventas</span>
              <span className="font-semibold">${reportData.monthly.revenue.toFixed(2)}</span>
            </div>
            <div className="flex justify-between">
              <span className="text-gray-600">Gastos</span>
              <span className="font-semibold text-red-600">-${reportData.monthly.expenses.toFixed(2)}</span>
            </div>
            <div className="border-t pt-3 flex justify-between">
              <span className="text-gray-600 font-semibold">Ganancia</span>
              <span className={`font-bold ${reportData.monthly.profit >= 0 ? 'text-green-600' : 'text-red-600'}`}>
                ${reportData.monthly.profit.toFixed(2)}
              </span>
            </div>
          </div>
        </div>

        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4 text-green-600">Reporte Total</h3>
          <div className="space-y-3">
            <div className="flex justify-between">
              <span className="text-gray-600">Ventas</span>
              <span className="font-semibold">${reportData.total.revenue.toFixed(2)}</span>
            </div>
            <div className="flex justify-between">
              <span className="text-gray-600">Gastos</span>
              <span className="font-semibold text-red-600">-${reportData.total.expenses.toFixed(2)}</span>
            </div>
            <div className="border-t pt-3 flex justify-between">
              <span className="text-gray-600 font-semibold">Ganancia</span>
              <span className={`font-bold ${reportData.total.profit >= 0 ? 'text-green-600' : 'text-red-600'}`}>
                ${reportData.total.profit.toFixed(2)}
              </span>
            </div>
          </div>
        </div>
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4">Top Productos Vendidos</h3>
          <div className="space-y-2">
            {Object.entries(
              sales.reduce((acc, sale) => {
                acc[sale.productName] = (acc[sale.productName] || 0) + sale.quantity;
                return acc;
              }, {})
            )
              .sort((a, b) => b[1] - a[1])
              .slice(0, 5)
              .map(([product, quantity], index) => (
                <div key={index} className="flex justify-between items-center">
                  <span className="text-gray-700">{index + 1}. {product}</span>
                  <span className="font-semibold">{quantity} unidades</span>
                </div>
              ))}
          </div>
        </div>

        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-lg font-semibold mb-4">Productos con Bajo Stock</h3>
          <div className="space-y-2">
            {inventory
              .map(item => ({
                ...item,
                totalStock: Object.values(item.sizes || {}).reduce((sum, qty) => sum + qty, 0)
              }))
              .filter(item => item.totalStock < 10)
              .sort((a, b) => a.totalStock - b.totalStock)
              .slice(0, 5)
              .map((item, index) => (
                <div key={index} className="flex justify-between items-center">
                  <span className="text-gray-700">{item.name}</span>
                  <span className={`font-semibold ${
                    item.totalStock < 5 ? 'text-red-600' : 'text-yellow-600'
                  }`}>
                    {item.totalStock} unidades
                  </span>
                </div>
              ))}
          </div>
        </div>
      </div>
    </div>
  );
}