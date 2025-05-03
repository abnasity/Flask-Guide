## Carousel Example
### Bootstrap 5 Carousel
<!-- Bootstrap 5 Carousel Example -->

<!-- Include Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
<!-- Include Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>




<div class="container my-5">
  <div id="heroCarousel" class="carousel slide" data-bs-ride="carousel" data-bs-interval="3000">

  -Carousel inner is impoertant to add the slides
  -Carousel item is important to add the slides
  -Carousel controls are important to add the next and previous buttons
  -Carousel indicators are important to add the dots
    
##    <!-- Carousel Inner -->
    <div class="carousel-inner">

 #     <!-- Slide 1 -->

      <div class="carousel-item active">
        <div class="row align-items-center">
          <div class="col-md-6">
            <img src="https://media.istockphoto.com/id/458617533/photo/pair-of-adidas.jpg?s=612x612&w=0&k=20&c=BvzSF7yJ_c72m04Ot_edBtn68A3zR9CV_rgR_HQQnBY=" class="d-block w-100" alt="adidas sneakers">
          </div>
          <div class="col-md-6">
            <div class="p-4">
              <h2>Stylish Adidas Sneakers</h2>
              <p>Explore our wide range of stylish Adidas sneakers for men. Choose from slip-ons, classics, and retro designs.</p>
            </div>
          </div>
        </div>
      </div>

   #    <!-- Slide 2 -->
      <div class="carousel-item">
        <div class="row align-items-center">
          <div class="col-md-6">
            <img src="https://media.istockphoto.com/id/1199648781/photo/new-samsung-galaxy-note-10-android-smartphone.jpg?s=612x612&w=0&k=20&c=OVoepdXp3ibbBHm5KoouSxskXZ3pvg6zJnF1EPoR1Hc=" class="d-block w-100" alt="samsung phone">
          </div>
          <div class="col-md-6">
            <div class="p-4">
              <h2>Latest Samsung Phones</h2>
              <p>Shop the newest Galaxy Z Fold, Flip, and Note series at unbeatable prices in Kenya.</p>
            </div>
          </div>
        </div>
      </div>

 #     <!-- Slide 3 -->
      <div class="carousel-item">
        <div class="row align-items-center">
          <div class="col-md-6">
            <img src="https://media.istockphoto.com/id/1316030712/photo/a-dior-store-at-the-bloor-yorkville-business-area-in-toronto.jpg?s=612x612&w=0&k=20&c=kErlBucF2LX3RzDgZF46rJUnsMS9CO8T5sQrztQ2KVI=" class="d-block w-100" alt="Dior fashion">
          </div>
          <div class="col-md-6">
            <div class="p-4">
              <h2>Elegant Dior Designs</h2>
              <p>Step into luxury with stylish, bold, and sophisticated fashion from Dior.</p>
            </div>
          </div>
        </div>
      </div>

 #     <!-- Slide 4 -->
      <div class="carousel-item">
        <div class="row align-items-center">
          <div class="col-md-6">
            <img src="https://media.istockphoto.com/id/458968161/photo/preparing-rolex-window-shop.jpg?s=612x612&w=0&k=20&c=oQe3jzDVoJA2kX-09tx7fOEa478qoKIKF7Bciteuj8U=" class="d-block w-100" alt="Rolex watches">
          </div>
          <div class="col-md-6">
            <div class="p-4">
              <h2>Luxury Rolex Watches</h2>
              <p>Discover timeless elegance with Rolex. Explore collections built on precision and prestige.</p>
            </div>
          </div>
        </div>
      </div>

  #  </div> <!-- /.carousel-inner -->

  #  <!-- Controls -->
    <button class="carousel-control-prev" type="button" data-bs-target="#heroCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#heroCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
    
  </div>
</div>
