#Proyecto LogiTrack

Docker code:
`docker run --name postgres-logitrack -e POSTGRES_PASSWORD=admin123 -e POSTGRES_USER=postgres -e POSTGRES_DB=logitrack -p 5433:5432 -d postgres`

SQL para agregar data de prueba
-- Customers
INSERT INTO Customer (customerId, fullName, NIT, email, address, active)
VALUES 
(1, 'Comercial El Buen Precio', '1234567890', 'contacto@buenprecio.com', 'Zona 1, Ciudad de Guatemala', TRUE),
(2, 'Distribuidora La Económica', '9876543210', 'ventas@economica.com', 'Mixco, Guatemala', FALSE),
(3, 'Supermercado La Favorita', '555666777', 'info@favorita.com', 'Antigua Guatemala', TRUE),
(4, 'Ferretería El Martillo', '111222333', 'ventas@martillo.com', 'Quetzaltenango', TRUE);

-- Products (Category_product BEVERAGES y SNACKS)
INSERT INTO Product (productId, name, description, price, category, active)
VALUES
(1, 'Coca Cola 1L', 'Bebida gaseosa 1 litro', 10.00, 'BEVERAGES', TRUE),
(2, 'Pepsi 1L', 'Bebida gaseosa 1 litro', 9.50, 'BEVERAGES', TRUE),
(3, 'Papas Fritas Lays', 'Bolsa de papas fritas 150g', 7.00, 'SNACKS', TRUE),
(4, 'Chocolatina Jet', 'Chocolatina de 12g', 2.50, 'SNACKS', FALSE);

-- Orders (order_status Pending, Processing, Completed y Cancelled)
INSERT INTO Orders (orderId, customerId, orderDate, status, totalAmount)
VALUES
(1, 1, '2025-11-20', 'Pending', 19.50),
(2, 2, '2025-11-21', 'Processing', 7.00),
(3, 3, '2025-11-22', 'Completed', 10.00),
(4, 4, '2025-11-23', 'Cancelled', 2.50);

-- OrderItems
INSERT INTO OrderItem (orderItemId, orderId, productId, quantity, unitPrice, subtotal)
VALUES
(1, 1, 1, 1, 10.00, 10.00),
(2, 1, 2, 1, 9.50, 9.50),
(3, 2, 3, 1, 7.00, 7.00),
(4, 4, 4, 1, 2.50, 2.50);

-- Payments (Payment_method Cash, Card, Transfer)
INSERT INTO Payment (paymentId, orderId, paymentDate, amount, method)
VALUES
(1, 1, '2025-11-22', 10.00, 'Card'),
(2, 1, '2025-11-23', 9.50, 'Cash'),
(3, 3, '2025-11-23', 10.00, 'Transfer'),
(4, 2, '2025-11-24', 7.00, 'Card');
