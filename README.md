
package com.omkar.ai

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

val Navy = Color(0xFF071A38)
val Blue = Color(0xFF60A5FA)
val Panel = Color(0xFF10294D)

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            var page by remember { mutableStateOf("Home") }

            MaterialTheme(
                colorScheme = darkColorScheme(
                    primary = Blue,
                    background = Navy,
                    surface = Panel
                )
            ) {
                Column(
                    modifier = Modifier
                        .fillMaxSize()
                        .background(Navy)
                        .padding(20.dp)
                ) {
                    when (page) {
                        "Home" -> {
                            Text(
                                "OMKAR AI",
                                color = Color.White,
                                fontSize = 32.sp
                            )

                            Text(
                                "Your Personal AI Assistant",
                                color = Blue
                            )

                            Spacer(Modifier.height(30.dp))

                            Button(
                                onClick = { page = "Chat" }
                            ) {
                                Text("AI Chat")
                            }

                            Button(
                                onClick = { page = "Study" }
                            ) {
                                Text("SSC Study")
                            }
                        }

                        "Chat" -> {
                            var message by remember {
                                mutableStateOf("")
                            }

                            Text("OMKAR AI CHAT", color = Blue)

                            OutlinedTextField(
                                value = message,
                                onValueChange = { message = it },
                                label = { Text("Ask anything") }
                            )

                            Text(
                                "AI backend connection required for real replies.",
                                color = Color.White
                            )

                            Button(onClick = { page = "Home" }) {
                                Text("Back")
                            }
                        }

                        "Study" -> {
                            Text(
                                "SSC CLASS 10",
                                color = Blue,
                                fontSize = 24.sp
                            )

                            val subjects = listOf(
                                "Maths Part 1",
                                "Maths Part 2",
                                "Science Part 1",
                                "Science Part 2",
                                "History & Political Science",
                                "Geography",
                                "English",
                                "Marathi",
                                "Hindi"
                            )

                            subjects.forEach {
                                Card(
                                    modifier = Modifier
                                        .fillMaxWidth()
                                        .padding(vertical = 4.dp),
                                    colors = CardDefaults.cardColors(
                                        containerColor = Panel
                                    )
                                ) {
                                    Text(
                                        it,
                                        color = Color.White,
                                        modifier = Modifier.padding(12.dp)
                                    )
                                }
                            }

                            Button(onClick = { page = "Home" }) {
                                Text("Back")
                            }
                        }
                    }
                }
            }
        }
    }
}

