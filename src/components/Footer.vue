<template>
    <footer class="footer">
        <div class="footer-footer">
           <div class="footer-contact">
                <span class="footer-contact-span">
                    Liên hệ với tôi qua    
                </span>
                <ul>
                    <li class="footer-contact-item">
                        <i class="far fa-envelope"></i>
                        <a class="footer-contact-item-link" href="">hocb1906673@student.ctu.edu.vn</a>
                    </li>
                    <li class="footer-contact-item">
                        <i class="fas fa-phone"></i>
                        <a class="footer-contact-item-link" href="">0123456789</a>
                    </li>
                </ul>
           </div>
           <div class="footer-contact">
                <span class="footer-contact-span">
                    Theo dõi tôi trên   
                </span>
                <ul>
                    <li class="footer-contact-item">
                        <i class="fab fa-facebook"></i>
                        <a class="footer-contact-item-link" href="">Facebook</a>
                    </li>
                    <li class="footer-contact-item">
                        <i class="fab fa-instagram"></i>
                        <a class="footer-contact-item-link" href="">Instagram</a>
                    </li>
                    <li class="footer-contact-item">
                        <i class="fab fa-youtube"></i>
                        <a class="footer-contact-item-link" href="">Youtube</a>
                    </li>
                </ul>
            </div>
       </div>
           
       <div class="footer-span">
            <span >
                © Bản quyền thuộc về Nguyễn Võ Thái Học
            </span>
       </div>
</footer>
</template>

<script>
export default {
    name:"Footer"
}
</script>

<style>
.footer{
    width: 100%;
    background: rgba(19, 19, 19, 0.47);
    border-top: 2px solid rgba(0, 0, 0, 0.545);
    margin-top: 100px;
    margin: 0 auto;
    height: auto;
}

.footer-footer{
    margin: 0 auto;
    display: flex;
    justify-content: center;
}

.footer-contact{
    padding-left: 60px;
    margin-top: 16px;
}

.footer-contact-span{
    font-size: 20px;
}

.footer-contact-item{
    list-style: none;
    font-size: 20px;
    display: flex;
    margin-top: 8px;
}

.footer-contact-item-link{
    color: rgb(32, 30, 30);
    padding-left: 15px;
    text-decoration: none;
}

.fa-envelope{
    color:rgb(23, 213, 219);
    margin-left: -28px;
}

.fa-phone{
    color: rgb(224, 48, 48);
    margin-left: -28px;
}

.fa-facebook{
    color: #0a34bd;
    margin-left: -24px;
}

.fa-instagram{
    color: rgb(228, 28, 168);
    margin-left: -24px;
}

.fa-youtube{
    margin-left: -24px;
    color: rgb(173, 15, 15);
}

.footer-span{
    text-align: center;
    font-size: 20px;
    color: white;
    padding-bottom: 16px;
}

span, a.footer-contact-item-link{
    color: black;
}

a.footer-contact-item-link:hover{
    color: white;
}

.far, .fab, .fas {
    padding-top: 6px;
}

</style>
