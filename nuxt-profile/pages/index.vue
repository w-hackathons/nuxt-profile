<template>
  <div>
    <header class="header">
        <h1 class="site-title">
            <a href="index.html">
                <p>名前</p>
            </a>
        </h1>
        <nav>
            <ul>
                <li><NuxtLink to="/about">About</NuxtLink></li>
                <li><a href="#images">images</a></li>
            </ul>
        </nav>
    </header>

    <!-- メインの情報 -->
    <main>
        <div class="container">
            <img src="https://www.pakutaso.com/shared/img/thumb/redsg13302_TP_V.jpg" alt="トプ画"/>
        </div>

        <section id="about" class="container__about">
            <h2 class="section-title">About</h2>
            <div class="container__about__content">
                <img src="https://1.bp.blogspot.com/-lQvVaZVuCfs/XvcI4m2KdKI/AAAAAAABZts/6a_b9K3DrscSuAa_9lY6dDEb313PNnklwCNcBGAsYHQ/s400/megane_hikaru_woman.png" alt="テキストテキストテキスト"/>
                <div class="container__about--text">
                    <h3 class="content-title">自分の名前</h3>
                    <p>
                        自分は○○が趣味でよく○○しています。<br>
                        学生で現在○○○○大学の○○学部、○○学科○年に所属しています。<br>
                        現在はプログラミングを学んでいます！
                    </p>
                </div>
            </div>
        </section>

        <section id="images" class="container__images">
            <h2 class="section-title">Images</h2>
            <ul>
                <li>
                    <img src="https://1.bp.blogspot.com/-29VIHWBD8WA/Xv3UG8pXrwI/AAAAAAABZz0/1s5ueoDxBKI6C4K-a_Djv9OkO-BlPwuxwCNcBGAsYHQ/s400/city_night_yoruno_machi.png" alt="テキストテキストテキスト"/>
                    <h3 class="content-title">夜景</h3>
                    <p>○○で撮影しました！</p>
                </li>
                <li>
                    <img src="https://4.bp.blogspot.com/-_3_Hua-2ehY/WI1zf3hT50I/AAAAAAABBZI/FqqR58-_c0c_kQf50_o2Y3Uydl7SjwnIwCLcB/s400/hanabi_kaichu.png" alt="テキストテキストテキスト"/>
                    <h3 class="content-title">花火</h3>
                    <p>○○への旅行で撮りました！</p>
                </li>
                <li>
                    <img src="https://1.bp.blogspot.com/-LDQjratJYoM/YHDkNRgd1XI/AAAAAAABdl8/h5yxEkLKmBcXC6-GXJsoOIzJsCDWd5sMACNcBGAsYHQ/s400/landmark_tausyubetsu_bridge.png" alt="テキストテキストテキスト"/>
                    <h3 class="content-title">散歩コースの川</h3>
                    <p>いつもここを散歩してます！</p>
                </li>
            </ul>
        </section>
    </main>

    <!-- フッター -->
    <footer id="footer">
        {{ data }}
    </footer>
  </div>
</template>

<script setup>
const today = new Date();
    const year = today.getFullYear();
    const month = today.getMonth() + 1;
    const day = today.getDate();
    const date = "&copy;" + year + "年" + month + "月" + day + "日";
    // document.getElementById("footer").innerHTML = date;
    const data = `${year}年${month}月${day}日`;
</script>

<style lang="scss" scoped>
@charset "UTF-8";

/*-------------------------------------------
デフォルトのスタイルを設定（基本いじらない）
-------------------------------------------*/
html {
    font-size: 100%;
}
body {
    color: #383e45;
    font-size: 0.9rem;
}
a {
    text-decoration: none;
}
img {
    max-width: 100%;
}
li {
    list-style: none;
}

/*-------------------------------------------
コンテンツ事のスタイル変数
-------------------------------------------*/
$content-max-width: 960px;
$max_sp: 600px;

/*-------------------------------------------
共通のスタイル
-------------------------------------------*/

/* コンテンツの範囲を共通で持つ */
@mixin contents($max-width: $content-max-width) {
    max-width: $max-width;
    margin: 0 auto 100px auto;
    padding: 0 4%;
    text-align: center;
}

/* モバイル版のメディアクエリを持つ */
@mixin max_sp {
    @media screen and (max-width: $max_sp) {
        @content;
    }
}

/*-------------------------------------------
ヘッダー
-------------------------------------------*/
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    margin-left: 2rem;
    margin-right: 2rem;
    ul {
        display: flex;
        padding: 10px 0;
    }
    li {
        margin-left: 30px;
        a {
            color: #24292e;
            &:hover {
                opacity: 0.7;
            }
        }
    }
}

/*-------------------------------------------
複数使うスタイル
-------------------------------------------*/
.site-title {
    line-height: 1px;
    padding: 10px 0;
    a {
        display: block;
    }
}
.section-title {
    display: inline-block;
    font-size: 2rem;
    text-align: center;
    margin-bottom: 60px;
    border-bottom: solid 1px #383e45;
}
.content-title {
    font-size: 1rem;
    margin: 10px 0;
}

/*-------------------------------------------
body内の全体のスタイル
-------------------------------------------*/
.container {
    margin-bottom: 80px;
    img {
        width: 100%;
        height: 600px;
        object-fit: cover;
    }
    /*-------------------------------------------
    About
    -------------------------------------------*/
    &__about {
        @include contents;
        &__content {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            margin-right: 30px;
        }
        &--text {
            text-align: left;
        }
    }
    /*-------------------------------------------
    images
    -------------------------------------------*/
    &__images {
        @include contents;
        ul {
            display: flex;
            justify-content: space-between;
        }
        li {
            width: 32%;
        }
    }
}

/*-------------------------------------------
footer
-------------------------------------------*/
#footer {
    font-size: 0.5rem;
    padding: 10px 0;
    text-align: center;
}

/*-------------------------------------------
モバイル版の見た目にする
-------------------------------------------*/
@include max_sp {
    .container {
        img {
            // height: calc(100vh - 60px);
            height: 100vh;
        }
        &__about {
            &__content {
                flex-direction: column;
            }
            img {
                margin-right: 0;
            }
        }
        &__images {
            ul {
                flex-direction: column;
            }
            li {
                width: 100%;
                margin-bottom: 30px;
            }
        }
    }
}
</style>