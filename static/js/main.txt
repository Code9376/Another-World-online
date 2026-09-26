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
// 回到顶部按钮
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