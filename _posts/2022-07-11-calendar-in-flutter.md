---
layout: post
title: "How to generate a simple calendar in Google Flutter?"
date: 2022-07-11 06:00:00 +0530
categories: flutter
---

Here is a simple code snippet to generate a simple calendar widget in Google Flutter.

```dart
import 'package:flutter/material.dart';
import 'package:slcalendar/domain/calendar_event.dart';

class MonthView extends StatelessWidget {
  final int year, month;
  final List<CalendarEvent>? events;
  const MonthView({
    Key? key,
    required this.year,
    required this.month,
    this.events = const [],
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    var date = DateTime(year, month, 1);
    while (date.weekday > DateTime.monday) {
      date = date.add(const Duration(days: -1));
    }
    return Column(
      children: List.generate(6, (index) => index).map(
        (_) {
          return Expanded(
            child: Container(
              decoration: BoxDecoration(
                border: Border(
                  bottom: BorderSide(color: Colors.grey.withOpacity(.25)),
                ),
              ),
              child: Row(
                children: List.generate(7, (index) => 7).map(
                  (_) {
                    final oldDate = date;
                    final colorScheme = Theme.of(context).colorScheme;
                    date = date.add(const Duration(days: 1));
                    var fontColor = colorScheme.onSurface;
                    if (oldDate.weekday == DateTime.sunday) {
                      fontColor = colorScheme.error;
                    }
                    var fontWeight = FontWeight.normal;
                    final eventsForDay = events
                            ?.where(
                              (event) =>
                                  oldDate.day == event.date &&
                                  oldDate.month == month,
                            )
                            .toList() ??
                        [];
                    var backgroundColor = Colors.transparent;
                    if (eventsForDay.isNotEmpty) {
                      backgroundColor = eventsForDay[0].color;
                      fontWeight = FontWeight.bold;
                      fontColor = Colors.white;
                    }
                    return Flexible(
                      fit: FlexFit.tight,
                      child: Stack(
                        children: [
                          Positioned.fill(
                            child: AspectRatio(
                              aspectRatio: 1,
                              child: Container(
                                margin: const EdgeInsets.all(8),
                                decoration: BoxDecoration(
                                  shape: BoxShape.circle,
                                  color: backgroundColor,
                                ),
                              ),
                            ),
                          ),
                          Positioned.fill(
                            child: Center(
                              child: Text(
                                '${oldDate.day}',
                                style: TextStyle(
                                  color: fontColor,
                                  fontSize: eventsForDay.isEmpty ? 18 : 24,
                                  fontWeight: fontWeight,
                                ),
                              ),
                            ),
                          ),
                        ],
                      ),
                    );
                  },
                ).toList(),
              ),
            ),
          );
        },
      ).toList(),
    );
  }
}
```

Feel free to use it in your next project!

### Happy coding!