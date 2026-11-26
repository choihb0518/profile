# profile

from PIL import Image, ImageDraw
import math

W, H = 600, 120
frames = []

for frame in range(12):
    img = Image.new("RGBA", (W, H), (0, 0, 0, 0))
    draw = ImageDraw.Draw(img)

    x = 30 + frame * 42
    y = 55

    # 걷는 다리 움직임
    leg = math.sin(frame * math.pi / 2) * 8

    # 꼬리
    draw.line(
        [(x - 20, y - 5),
         (x - 32, y - 20 + leg)],
        fill="#333333", width=5
    )

    # 몸통
    draw.ellipse(
        (x - 20, y - 12, x + 25, y + 15),
        fill="#333333"
    )

    # 머리
    draw.ellipse(
        (x + 15, y - 28, x + 48, y + 5),
        fill="#333333"
    )

    # 귀
    draw.polygon(
        [(x + 18, y - 23),
         (x + 19, y - 38),
         (x + 30, y - 25)],
        fill="#333333"
    )

    draw.polygon(
        [(x + 35, y - 25),
         (x + 47, y - 37),
         (x + 45, y - 18)],
        fill="#333333"
    )

    # 눈
    draw.ellipse(
        (x + 38, y - 16, x + 42, y - 12),
        fill="white"
    )

    # 다리
    for offset, direction in [(-10, 1), (12, -1)]:
        lx = x + offset
        draw.line(
            [(lx, y + 8),
             (lx + leg * direction, y + 25)],
            fill="#333333", width=5
        )

    frames.append(img)

frames[0].save(
    "cat-walk.gif",
    save_all=True,
    append_images=frames[1:],
    duration=100,
    loop=0,
    disposal=2,
    transparency=0
)

print("🐱 cat-walk.gif 생성 완료!")


print("🐱 cat-walk.gif 생성 완료!")

<div align="center">

# 🐱 Welcome to my GitHub!

<img src="./cat-walk.gif" width="600" alt="Walking cat animation">

### Thanks for visiting! ✨
