<html>
<html lang="en">
<h1>Shrutika Sawankar</h1>
<h2>USN : CS25177</h2>
<head>
    <meta charset="UTF-8">
    <title>Skyline Properties</title>

    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

        <style>
        body {
            background-color: #f8f9fa;
        }

        .sidebar {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }

        .card {
            transition: 0.3s;
        }

        .card:hover {
            transform: scale(1.03);
        }

        .property-img {
            height: 200px;
            object-fit: cover;
        }
    </style>
</head>

<body>


<nav class="navbar navbar-dark bg-dark">
    <div class="container-fluid">
        <span class="navbar-brand mb-0 h1">Skyline Properties</span>
    </div>
</nav>

<div class="container mt-4">
    <div class="row">

                <div class="col-md-3">
            <div class="sidebar">
                <h5>Filters</h5>

                <label>Price</label>
                <select id="priceFilter" class="form-select mb-3">
                    <option value="all">All</option>
                    <option value="low">Below 50L</option>
                    <option value="mid">50L - 1Cr</option>
                    <option value="high">Above 1Cr</option>
                </select>

                <label>BHK</label>
                <select id="bhkFilter" class="form-select">
                    <option value="all">All</option>
                    <option value="1">1 BHK</option>
                    <option value="2">2 BHK</option>
                    <option value="3">3 BHK</option>
                </select>
            </div>
        </div>

                <div class="col-md-9">
            <div class="row" id="propertyList">

                                <div class="col-md-6 mb-4 property" data-price="low" data-bhk="1">
                    <div class="card">
                        <img src="https://via.placeholder.com/400x200" class="card-img-top property-img">
                        <div class="card-body">
                            <h5>1 BHK Apartment</h5>
                            <p>Price: ₹40 Lakhs</p>
                            <button class="btn btn-primary" onclick="showDetails('1 BHK Apartment', '₹40 Lakhs', 'Nagpur')">View Details</button>
                        </div>
                    </div>
                </div>

                                <div class="col-md-6 mb-4 property" data-price="mid" data-bhk="2">
                    <div class="card">
                        <img src="https://via.placeholder.com/400x200" class="card-img-top property-img">
                        <div class="card-body">
                            <h5>2 BHK Flat</h5>
                            <p>Price: ₹75 Lakhs</p>
                            <button class="btn btn-primary" onclick="showDetails('2 BHK Flat', '₹75 Lakhs', 'Pune')">View Details</button>
                        </div>
                    </div>
                </div>

                                <div class="col-md-6 mb-4 property" data-price="high" data-bhk="3">
                    <div class="card">
                        <img src="https://via.placeholder.com/400x200" class="card-img-top property-img">
                        <div class="card-body">
                            <h5>3 BHK Villa</h5>
                            <p>Price: ₹1.5 Crore</p>
                            <button class="btn btn-primary" onclick="showDetails('3 BHK Villa', '₹1.5 Crore', 'Mumbai')">View Details</button>
                        </div>
                    </div>
                </div>

            </div>
        </div>

    </div>
</div>

<div class="modal fade" id="propertyModal">
    <div class="modal-dialog">
        <div class="modal-content">

            <div class="modal-header">
                <h5 id="modalTitle"></h5>
                <button class="btn-close" data-bs-dismiss="modal"></button>
            </div>

            <div class="modal-body">
                <p id="modalPrice"></p>
                <p id="modalLocation"></p>
            </div>

        </div>
    </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

<script>
    const priceFilter = document.getElementById("priceFilter");
    const bhkFilter = document.getElementById("bhkFilter");

    priceFilter.addEventListener("change", filterProperties);
    bhkFilter.addEventListener("change", filterProperties);

    function filterProperties() {
        const price = priceFilter.value;
        const bhk = bhkFilter.value;

        const properties = document.querySelectorAll(".property");

        properties.forEach(property => {
            const pPrice = property.getAttribute("data-price");
            const pBhk = property.getAttribute("data-bhk");

            let show = true;

            if (price !== "all" && price !== pPrice) show = false;
            if (bhk !== "all" && bhk !== pBhk) show = false;

            property.style.display = show ? "block" : "none";
        });
    }

    function showDetails(title, price, location) {
        document.getElementById("modalTitle").innerText = title;
        document.getElementById("modalPrice").innerText = "Price: " + price;
        document.getElementById("modalLocation").innerText = "Location: " + location;

        let modal = new bootstrap.Modal(document.getElementById("propertyModal"));
        modal.show();
    }
</script>

</body>
</html># Experential-Learning-mode-3
