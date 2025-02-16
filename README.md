 قارورة استيراد قارورة، طلب، jsonify
استيراد إعادة

التطبيق = Flask(__name__)

def is_strong_password(كلمة المرور):
    إذا كان len(كلمة المرور) < 8:
        العودة كاذبة
    إذا لم يكن re.search(r'[AZ]', كلمة المرور):
        العودة كاذبة
    إذا لم يكن re.search(r'[az]', كلمة المرور):
        العودة كاذبة
    إذا لم يكن re.search(r'[0-9]', كلمة المرور):
        العودة كاذبة
    إذا لم يكن re.search(r'[\W_]', كلمة المرور):
        العودة كاذبة
    العودة صحيح

@app.route('/signup', methods=['POST'])
def signup():
    البيانات = request.json
    اسم المستخدم = data.get('اسم المستخدم')
    كلمة المرور = data.get('كلمة المرور')
    
    إذا لم يكن اسم المستخدم أو كلمة المرور:
        return jsonify({'error': 'اسم المستخدم وكلمة المرور مطلوبان!'}), 400
    
    إذا لم يكن is_strong_password(كلمة المرور):
        return jsonify({'error': 'كلمة المرور لا تلبي متطلبات القوة!'}), 400
    
    # هنا عادةً ما تقوم بحفظ المستخدم في قاعدة البيانات
    # بالنسبة لهذا المثال، سنعيد فقط رسالة النجاح
    return jsonify({'message': 'تم تسجيل المستخدم بنجاح!'}), 201

إذا كان __name__ == '__main__':
    تطبيق.تشغيل(debug=True)
    body {
    text-align: center;
    background-color: #222;
    color: white;
    font-family: Arial, sans-serif;
}

.game-container {
    position: relative;
    margin: auto;
    width: 300px;
    height: 400px;
    background: #000;
    border: 2px solid #fff;
}

canvas {
    display: block;
    background-color: #444;
}
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
canvas.width = 300;
canvas.height = 400;

let apple = { x: 150, y: 50, radius: 10, dy: 2 };
let gameActive = false;

function drawApple() {
    ctx.fillStyle = "red";
    ctx.beginPath();
    ctx.arc(apple.x, apple.y, apple.radius, 0, Math.PI * 2);
    ctx.fill();
}

function updateGame() {
    if (!gameActive) return;
    
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawApple();
    apple.y += apple.dy;
    
    if (apple.y > canvas.height) {
        apple.y = 50;
    }
    
    requestAnimationFrame(updateGame);
}

document.getElementById("startGame").addEventListener("click", () => {
    gameActive = true;
    updateGame();
});
