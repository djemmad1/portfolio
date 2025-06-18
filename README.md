# portfolio
import 'package:flutter/material.dart';

class WireframeScreen extends StatelessWidget {
  const WireframeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // 1. الشريط العلوي (AppBar)
      appBar: AppBar(
        backgroundColor: Colors.white,
        elevation: 0,
        leading: IconButton(
          icon: const Icon(Icons.close, color: Colors.black),
          onPressed: () {
            // يمكنك إضافة وظيفة هنا، مثل العودة للشاشة السابقة
          },
        ),
        actions: [
          IconButton(
            icon: const Icon(Icons.more_vert, color: Colors.black),
            onPressed: () {},
          ),
        ],
      ),

      // 2. محتوى الصفحة (Body)
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // 3. شريط البحث
            Row(
              children: [
                const Expanded(
                  child: TextField(
                    decoration: InputDecoration(
                      hintText: 'ابحث هنا...',
                      border: OutlineInputBorder(),
                    ),
                  ),
                ),
                const SizedBox(width: 8),
                ElevatedButton(
                  onPressed: () {},
                  style: ElevatedButton.styleFrom(
                    padding: const EdgeInsets.symmetric(
                        horizontal: 20, vertical: 15),
                  ),
                  child: const Text('YES'),
                ),
              ],
            ),
            const SizedBox(height: 20),

            // 4. أماكن الصور
            Row(
              children: [
                Expanded(child: _buildImagePlaceholder()),
                const SizedBox(width: 16),
                Expanded(child: _buildImagePlaceholder()),
              ],
            ),
            const SizedBox(height: 20),

            // 5. المحتوى النصي
            const Text(
              'هنا يأتي المحتوى النصي الخاص بالتطبيق. يمكن أن يكون وصفًا للمنتج أو مقالة أو أي معلومات أخرى تريد عرضها للمستخدم في هذا الجزء من الشاشة.',
              style: TextStyle(fontSize: 16, color: Colors.black54),
            ),
            const SizedBox(height: 20),

            // 6. أدوات التصفح (Carousel Indicators)
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                const Icon(Icons.arrow_back_ios, color: Colors.grey),
                const SizedBox(width: 16),
                _buildCarouselIndicator(isActive: true),
                _buildCarouselIndicator(),
                _buildCarouselIndicator(),
                const SizedBox(width: 16),
                const Icon(Icons.arrow_forward_ios, color: Colors.grey),
              ],
            ),
            const Spacer(), // لدفع شريط التنقل السفلي إلى الأسفل
          ],
        ),
      ),

      // 7. شريط التنقل السفلي (BottomNavigationBar)
      bottomNavigationBar: BottomNavigationBar(
        type: BottomNavigationBarType.fixed, // لإظهار كل الأيقونات
        items: const [
          BottomNavigationBarItem(
            icon: Icon(Icons.refresh),
            label: 'تحديث',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.email_outlined),
            label: 'البريد',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.bookmark_border),
            label: 'المحفوظات',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.share),
            label: 'مشاركة',
          ),
        ],
      ),
    );
  }

  // ويدجت مساعد لإنشاء أماكن الصور
  Widget _buildImagePlaceholder() {
    return AspectRatio(
      aspectRatio: 1, // لجعل العرض والطول متساويين
      child: Container(
        decoration: BoxDecoration(
          color: Colors.grey[200],
          border: Border.all(color: Colors.grey[400]!),
        ),
        child: const Icon(Icons.image_outlined,
            size: 40, color: Colors.grey),
      ),
    );
  }

  // ويدجت مساعد لإنشاء مؤشرات التصفح
  Widget _buildCarouselIndicator({bool isActive = false}) {
    return Container(
      margin: const EdgeInsets.symmetric(horizontal: 4),
      width: 10,
      height: 10,
      decoration: BoxDecoration(
        color: isActive ? Colors.blue : Colors.grey[300],
        shape: BoxShape.rectangle, //
        border: Border.all(color: Colors.grey[400]!)
      ),
    );
  }
}
A portfolio website designed for a flutter developer
