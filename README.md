from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer, Image, Table, TableStyle
from reportlab.lib.pagesizes import A4
from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle
from reportlab.lib.enums import TA_CENTER
from reportlab.lib import colors

# File path
pdf_file = "/mnt/data/AURUM_Basra_App_Requirements.pdf"

# Document setup
doc = SimpleDocTemplate(pdf_file, pagesize=A4)
styles = getSampleStyleSheet()
styles.add(ParagraphStyle(name="CenterTitle", fontSize=20, alignment=TA_CENTER, spaceAfter=20))
styles.add(ParagraphStyle(name="SectionHeader", fontSize=14, spaceAfter=10, textColor=colors.HexColor("#333333")))

story = []

# Logo
logo_path = "/mnt/data/677B07B4-E62E-437E-882E-E0ABCB528498.jpeg"
story.append(Image(logo_path, width=120, height=120))
story.append(Spacer(1, 20))

# Title
story.append(Paragraph("AURUM البصرة", styles["CenterTitle"]))
story.append(Spacer(1, 20))

# Introduction
story.append(Paragraph("وثيقة المتطلبات الأولية لتطبيق <b>AURUM البصرة</b> – نسخة أولية.", styles["Normal"]))
story.append(Spacer(1, 20))

# Sections
sections = [
    ("1) الهوية البصرية", [
        "الاسم: AURUM البصرة",
        "الألوان المقترحة: الأسود – الذهبي – الأبيض",
        "الخطوط: عربية أنيقة + إنجليزية حديثة",
        "اللوغو: مرفق أعلى الوثيقة"
    ]),
    ("2) التطبيق (العميل)", [
        "واجهة متجر إلكتروني (ساعات يد + محافظ رجالية).",
        "صفحة رئيسية (عروض – منتجات مميزة – أقسام).",
        "تفاصيل المنتج (صور متعددة – وصف – السعر – الكمية).",
        "إضافة للسلة والدفع (أونلاين + عند الاستلام).",
        "متابعة حالة الطلب عبر الحساب."
    ]),
    ("3) لوحة التاجر", [
        "رفع منتجات جديدة (اسم – وصف – صور – سعر – كمية).",
        "تعديل وحذف المنتجات.",
        "إدارة الطلبات (قيد التجهيز – تم الشحن – تم التسليم)."
    ]),
    ("4) لوحة الإدارة (الأدمن)", [
        "التحكم في المنتجات والفئات.",
        "مراجعة الطلبات والمدفوعات.",
        "متابعة التقارير والمبيعات."
    ]),
    ("5) المزايا التقنية المقترحة", [
        "تطوير بواجهة موبايل باستخدام Flutter (iOS + Android).",
        "واجهة API بخادم Node.js أو Laravel.",
        "قاعدة بيانات PostgreSQL.",
        "دفع إلكتروني (Visa/MasterCard/ApplePay) + خيار الدفع عند الاستلام.",
        "تكامل مع شركات شحن محلية وإقليمية."
    ]),
    ("6) الخطوة القادمة", [
        "بناء واجهات التصميم (UI Wireframes).",
        "تحضير قاعدة البيانات والـ API.",
        "تجهيز نسخة MVP للإطلاق التجريبي."
    ])
]

for title, items in sections:
    story.append(Paragraph(title, styles["SectionHeader"]))
    for item in items:
        story.append(Paragraph(f"- {item}", styles["Normal"]))
    story.append(Spacer(1, 15))

# Build PDF
doc.build(story)

pdf_file
متجر 
