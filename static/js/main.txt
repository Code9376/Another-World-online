document.addEventListener("DOMContentLoaded", function () {
  const intro = document.getElementById("intro");
  if (!intro) return;

  if (sessionStorage.getItem("introPlayed")) {
    intro.remove();
    return;
  }
  sessionStorage.setItem("introPlayed", "1");

  const line1 = document.getElementById("line1");
  const line2 = document.getElementById("line2");

  const text1 = "已成功与世界建立链接！";
  const text2 = "请享受在Another World的一分一秒。";
  const speed = 100;
  const gapBetweenLines = 400;
  const holdAfterFinish = 1200;
  const fadeDuration = 800;

  function typeText(el, text, callback) {
    let i = 0;
    function step() {
      if (i < text.length) {
        el.textContent += text.charAt(i);
        i++;
        setTimeout(step, speed);
      } else if (callback) {
        callback();
      }
    }
    step();
  }

  setTimeout(function () {
    typeText(line1, text1, function () {
      setTimeout(function () {
        typeText(line2, text2, function () {
          setTimeout(function () {
            intro.classList.add("hide");
            setTimeout(function () {
              intro.remove();
            }, fadeDuration);
          }, holdAfterFinish);
        });
      }, gapBetweenLines);
    });
  }, 2700);
});

document.addEventListener("DOMContentLoaded", function () {
  const title = document.querySelector(".data-title");
  if (!title) return;

  const text = title.dataset.title || title.textContent;
  title.textContent = "";
  let i = 0;

  (function type() {
    if (i < text.length) {
      title.textContent += text.charAt(i);
      i++;
      setTimeout(type, 150);
    }
  })();
});

document.addEventListener("DOMContentLoaded", function () {
  const mainImg = document.getElementById("data-img");
  const prev = document.querySelector(".thumb.prev");
  const next = document.querySelector(".thumb.next");
  const images = window.__dataImages;

  if (!mainImg || !images || images.length === 0) return;

  let index = 0;

  function show(i) {
    index = (i + images.length) % images.length;
    mainImg.src = images[index];
  }

  if (prev) prev.addEventListener("click", function () { show(index - 1); });
  if (next) next.addEventListener("click", function () { show(index + 1); });
});

document.addEventListener("DOMContentLoaded", function () {
  document.querySelectorAll(".data-image img").forEach(function (img) {
    img.addEventListener("contextmenu", function (e) {
      e.preventDefault();
    });
  });
});
    });
  }, 2700);
});
(function () {
  const btn = document.getElementById("back-to-top");
  if (!btn) return;

  window.addEventListener("scroll", function () {
    if (window.scrollY > 300) {
      btn.classList.add("visible");
    } else {
      btn.classList.remove("visible");
    }
  });

  btn.addEventListener("click", function () {
    window.scrollTo({ top: 0, behavior: "smooth" });
  });
})();
(function () {
  const title = document.querySelector(".data-title");
  if (title) {
    const text = title.dataset.title || title.textContent;
    title.textContent = "";
    let i = 0;
(function () {
  const mainImg = document.getElementById("data-img");
  const prev = document.querySelector(".thumb.prev");
  const next = document.querySelector(".thumb.next");
  const images = window.__dataImages;

  if (!mainImg || !images || images.length === 0) return;

  let index = 0;

  function show(i) {
    index = (i + images.length) % images.length;
    mainImg.src = images[index];
  }

  if (prev) prev.addEventListener("click", function () { show(index - 1); });
  if (next) next.addEventListener("click", function () { show(index + 1); });
})();

  const mainImg = document.getElementById("data-img");
  const thumbs = document.querySelectorAll(".thumb");
  if (mainImg && thumbs.length) {
    mainImg.src = thumbs[0].dataset.src;
    thumbs.forEach(function (btn) {
      btn.addEventListener("click", function () {
        mainImg.src = btn.dataset.src;
      });
    });
  }
})();
document.addEventListener("DOMContentLoaded", function () {
  document.querySelectorAll(".data-image img").forEach(function (img) {
    img.addEventListener("contextmenu", function (e) {
      e.preventDefault();
    });
  });
});