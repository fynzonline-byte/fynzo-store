# fynzo-store
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fynzo Online | Premium Store</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #000; color: #fff; font-family: sans-serif; }
        .product-card { background: #0d0d0d; border: 1px solid #1a1a1a; border-radius: 12px; overflow: hidden; }
        .modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.9); z-index: 100; justify-content: center; align-items: center; padding: 20px; }
        .modal.active { display: flex; }
    </style>
</head>
<body>

    <header class="p-5 text-center border-b border-zinc-900 bg-black sticky top-0 z-50">
        <h1 class="text-2xl font-bold tracking-tighter uppercase italic">Fynzo <span class="text-[#deff9a]">Online</span></h1>
        <p class="text-[10px] text-zinc-500 tracking-widest uppercase">Premium Dropshipping Catalog</p>
    </header>

    <div class="p-4 grid grid-cols-2 gap-4">
        
        <div class="product-card" onclick="openOrder('Naruto Sage Tee', '699', 'https://i.ibb.co/v4m0sR5/naruto-tee.jpg')">
            <img src="https://via.placeholder.com/400x500/111/fff?text=Upload+Photo+1" class="w-full h-48 object-cover">
            <div class="p-3 text-center">
                <h3 class="text-xs font-semibold truncate">Naruto Sage Tee</h3>
                <p class="text-[#deff9a] font-bold text-sm">&#8377;699</p>
            </div>
        </div>

        <div class="product-card" onclick="openOrder('Premium Gold Watch', '1299', 'https://i.ibb.co/zH7mZ5n/gold-watch.jpg')">
            <img src="https://via.placeholder.com/400x500/111/fff?text=Upload+Photo+2" class="w-full h-48 object-cover">
            <div class="p-3 text-center">
                <h3 class="text-xs font-semibold truncate">Premium Gold Watch</h3>
                <p class="text-[#deff9a] font-bold text-sm">&#8377;1299</p>
            </div>
        </div>

        <div class="product-card" onclick="openOrder('Airpods Pro 3', '999', 'https://i.ibb.co/C0mDq4G/airpods.jpg')">
            <img src="https://via.placeholder.com/400x500/111/fff?text=Upload+Photo+3" class="w-full h-48 object-cover">
            <div class="p-3 text-center">
                <h3 class="text-xs font-semibold truncate">Airpods Pro 3</h3>
                <p class="text-[#deff9a] font-bold text-sm">&#8377;999</p>
            </div>
        </div>

        <div class="product-card" onclick="openOrder('Fashion Jewelry', '299', 'https://i.ibb.co/KjkZ5fB/jewelry.jpg')">
            <img src="https://via.placeholder.com/400x500/111/fff?text=Upload+Photo+4" class="w-full h-48 object-cover">
            <div class="p-3 text-center">
                <h3 class="text-xs font-semibold truncate">Fashion Jewelry</h3>
                <p class="text-[#deff9a] font-bold text-sm">&#8377;299</p>
            </div>
        </div>

    </div>

    <div id="orderModal" class="modal">
        <div class="bg-zinc-900 p-6 rounded-2xl w-full max-w-sm border border-zinc-800">
            <h2 id="selectedProduct" class="text-xl font-bold text-[#deff9a]"></h2>
            <p id="selectedPrice" class="text-sm text-zinc-500 mb-4"></p>
            
            <div class="space-y-3">
                <input type="text" id="custName" placeholder="Aapka Naam" class="w-full p-3 bg-black border border-zinc-800 rounded-lg text-white outline-none">
                <input type="tel" id="custPhone" placeholder="Mobile Number" class="w-full p-3 bg-black border border-zinc-800 rounded-lg text-white outline-none">
                <textarea id="custAddress" placeholder="Pura Address" class="w-full p-3 bg-black border border-zinc-800 rounded-lg h-24 text-white outline-none"></textarea>
                <input type="text" id="custPin" placeholder="Pincode" class="w-full p-3 bg-black border border-zinc-800 rounded-lg text-white outline-none">
            </div>

            <div class="flex gap-2 mt-6">
                <button onclick="closeOrder()" class="flex-1 py-3 text-zinc-400">Cancel</button>
                <button onclick="sendOrder()" class="flex-1 py-3 bg-[#deff9a] text-black font-bold rounded-lg uppercase italic">Order on WhatsApp</button>
            </div>
        </div>
    </div>

    <script>
        let currentProduct = ""; 
        let currentPrice = "";
        let currentImg = "";
        let myNumber = "916367923005"; // Aapka number set hai

        function openOrder(name, price, img) {
            currentProduct = name; 
            currentPrice = price;
            currentImg = img;
            document.getElementById('selectedProduct').innerText = name;
            document.getElementById('selectedPrice').innerText = "Price: ₹" + price;
            document.getElementById('orderModal').classList.add('active');
        }

        function closeOrder() { 
            document.getElementById('orderModal').classList.remove('active'); 
        }

        function sendOrder() {
            const name = document.getElementById('custName').value;
            const phone = document.getElementById('custPhone').value;
            const address = document.getElementById('custAddress').value;
            const pin = document.getElementById('custPin').value;

            if(!name || !phone || !address || !pin) { 
                alert("Bhai, saari details bharo!"); 
                return; 
            }

            // Message format with Photo Link
            const msg = `*FYNZO ONLINE - NEW ORDER*%0A------------------%0A*Item:* ${currentProduct}%0A*Price:* ₹${currentPrice}%0A*Photo:* ${currentImg}%0A------------------%0A*Cust Name:* ${name}%0A*Cust Phone:* ${phone}%0A*Address:* ${address}%0A*Pincode:* ${pin}`;
            
            window.open(`https://wa.me/${myNumber}?text=${msg}`, '_blank');
        }
    </script>
</body>
</html>