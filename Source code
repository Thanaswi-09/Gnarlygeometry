import tkinter as tk
from tkinter import ttk, messagebox
import math
import cv2
from PIL import Image, ImageTk
import matplotlib.pyplot as plt
import matplotlib.patches as patches
import numpy as np
from mpl_toolkits.mplot3d import Axes3D
from mpl_toolkits.mplot3d.art3d import Poly3DCollection
from itertools import product, combinations
import pygame
class VideoBackgroundApp:
def __init__(self, root):
self.root = root
self.root.title("Video Background App")
self.root.geometry("900x700")
# Initialize pygame mixer
pygame.mixer.init()
pygame.mixer.music.load("C:/Users/DELL 7390 2 IN
1/Downloads/gaming-music-3-146305.mp3")
pygame.mixer.music.play(-1) # -1 to loop the music indefinitely
# Create a container for video background
self.video_container = tk.Label(root)
self.video_container.pack(fill="both", expand=True)
# Load the video and display the first frame
self.cap = cv2.VideoCapture("C:/Users/DELL 7390 2 IN 1/Downloads/Black Slate Grey
Gradient Color and Style Video Background.mp4")
# Create a container for the footer (optional)
self.footer_frame = ttk.Frame(root, height=50, padding=10)
self.footer_frame.pack(fill="x", expand=False, side="bottom")
# Create a run button in the footer
self.run_button = ttk.Button(self.footer_frame, text="RUN",
command=self.open_next_window)
self.run_button.pack(side="top") # You can adjust the position (e.g., "bottom")
# Footer video height (adjust based on your footer height and desired video area)
self.footer_video_height = 100
# Call show_frame after footer initialization
self.show_frame()
def show_frame(self):
# Display video frames
ret, frame = self.cap.read()
if ret:
frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
new_width = max(1, self.root.winfo_width())
video_height = self.root.winfo_height() - self.footer_frame.winfo_height()
new_height = max(1, video_height)
frame = cv2.resize(frame, (new_width, new_height))
cropped_frame = frame[:-self.footer_video_height, :]
img = ImageTk.PhotoImage(image=Image.fromarray(cropped_frame))
self.video_container.configure(image=img)
self.video_container.image = img
self.video_container.after(10, self.show_frame)
def open_next_window(self):
# Create the window for choosing the dimension
self.dimension_window = tk.Toplevel(self.root)
self.dimension_window.title("Choose Dimension")
self.dimension_window.geometry("300x300")
self.dimension_window.configure(bg="black") # Background color
# Buttons for selecting 2D or 3D shapes
ttk.Button(self.dimension_window, text="2D",
command=self.open_2d_window).pack(pady=10)
ttk.Button(self.dimension_window, text="3D",
command=self.open_3d_window).pack(pady=10)
def open_2d_window(self):
# Create the window for 2D shapes
self.dimension_window = tk.Toplevel(self.root)
self.dimension_window.title("2D Shapes")
self.dimension_window.geometry("300x200")
self.dimension_window.configure(bg="grey") # Background color
# Buttons for selecting 2D shapes
ttk.Button(self.dimension_window, text="CIR", command=self.draw_2d_cir).pack(pady=10)
ttk.Button(self.dimension_window, text="SQR",
command=self.draw_2d_sqr).pack(pady=10)
ttk.Button(self.dimension_window, text="AREA", command=self.run_2d).pack(pady=10)
def open_3d_window(self):
# Create the window for 3D shapes
self.dimension_window = tk.Toplevel(self.root)
self.dimension_window.title("3D Shapes")
self.dimension_window.geometry("300x200")
self.dimension_window.configure(bg="grey") # Background color
# Buttons for selecting 3D shapes
ttk.Button(self.dimension_window, text="CIR", command=self.draw_3d_cir).pack(pady=10)
ttk.Button(self.dimension_window, text="SQR",
command=self.draw_3d_sqr).pack(pady=10)
ttk.Button(self.dimension_window, text="AREA", command=self.run_3d).pack(pady=10)
def draw_2d_cir(self):
def draw_square_with_circles(square_length):
fig, ax = plt.subplots()
# Draw the square
square = plt.Rectangle((0, 0), square_length, square_length, linewidth=1,
edgecolor='black', facecolor='none')
ax.add_patch(square)
# Calculate circle radius
R = square_length * np.sqrt(2) / (4 + 2 * np.sqrt(2))
# Draw circles in corners
circle1 = plt.Circle((R, R), R, color='blue', fill=False)
ax.add_artist(circle1)
circle2 = plt.Circle((square_length - R, R), R, color='blue', fill=False)
ax.add_artist(circle2)
circle3 = plt.Circle((R, square_length - R), R, color='blue', fill=False)
ax.add_artist(circle3)
circle4 = plt.Circle((square_length - R, square_length - R), R, color='blue', fill=False)
ax.add_artist(circle4)
# Draw the fifth circle
fifth_circle = plt.Circle((square_length / 2, square_length / 2), R, color='blue', fill=False)
ax.add_artist(fifth_circle)
# Set axis limits and aspect ratio
ax.set_xlim(0, square_length)
ax.set_ylim(0, square_length)
ax.set_aspect('equal', adjustable='box')
# Turn off axis labels and ticks for a cleaner figure
ax.axis('off')
plt.show()
square_length = 5
draw_square_with_circles(square_length)
def draw_2d_sqr(self):
fig, ax = plt.subplots()
fig.set_size_inches(5, 5)
big_square = patches.Rectangle((0.1, 0.1), 0.8, 0.8, linewidth=2, edgecolor='black',
facecolor='none')
ax.add_patch(big_square)
small_square = patches.Rectangle((0.47, 0.47), 0.05, 0.05, linewidth=2, edgecolor='black',
facecolor='none')
ax.add_patch(small_square)
circle1 = patches.Circle((0.32, 0.315), 0.22, linewidth=2, edgecolor='black',
facecolor='none')
circle2 = patches.Circle((0.68, 0.32), 0.22, linewidth=2, edgecolor='black', facecolor='none')
circle3 = patches.Circle((0.32, 0.68), 0.22, linewidth=2, edgecolor='black', facecolor='none')
circle4 = patches.Circle((0.68, 0.68), 0.22, linewidth=2, edgecolor='black', facecolor='none')
ax.add_patch(circle1)
ax.add_patch(circle2)
ax.add_patch(circle3)
ax.add_patch(circle4)
plt.grid(False)
plt.axis('off')
plt.show()
def draw_3d_cir(self):
def plot_spheres_in_cube():
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d', facecolor='white')
size = 4
r = size / 2
centers = [
[r, r, r], [3 * r, r, r], [r, 3 * r, r], [3 * r, 3 * r, r],
[r, r, 3 * r], [3 * r, r, 3 * r], [r, 3 * r, 3 * r], [3 * r, 3 * r, 3 * r],
[2 * r, 2 * r, 2 * r]
]
sphere_surfaces = []
for i, center in enumerate(centers):
u, v = np.mgrid[0:2 * np.pi:20j, 0:np.pi:10j]
x = r * np.cos(u) * np.sin(v) + center[0]
y = r * np.sin(u) * np.sin(v) + center[1]
z = r * np.cos(v) + center[2]
color = 'grey' if i == 8 else 'lime'
sphere_surfaces.append(ax.plot_surface(x, y, z, color=color, alpha=0.6,
edgecolor='none', shade=True))
cube_range = [0, size*2]
for s, e in combinations(np.array(list(product(cube_range, cube_range, cube_range))),
2):
if np.sum(np.abs(s - e)) == cube_range[1] - cube_range[0]:
ax.plot3D(*zip(s, e), color="white")
vertices = np.array([
[cube_range[0], cube_range[0], cube_range[0]],
[cube_range[1], cube_range[0], cube_range[0]],
[cube_range[1], cube_range[1], cube_range[0]],
[cube_range[0], cube_range[1], cube_range[0]],
[cube_range[0], cube_range[0], cube_range[1]],
[cube_range[1], cube_range[0], cube_range[1]],
[cube_range[1], cube_range[1], cube_range[1]],
[cube_range[0], cube_range[1], cube_range[1]],
])
faces = [
[vertices[j] for j in [0, 1, 5, 4]],
[vertices[j] for j in [7, 6, 2, 3]],
[vertices[j] for j in [0, 3, 7, 4]],
[vertices[j] for j in [1, 2, 6, 5]],
[vertices[j] for j in [0, 1, 2, 3]],
[vertices[j] for j in [4, 5, 6, 7]],
]
face_collection = Poly3DCollection(faces, linewidths=1, edgecolors='white')
face_collection.set_facecolor((0, 0, 0, 0))
ax.add_collection3d(face_collection)
ax.view_init(30, 30)
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.set_box_aspect([1, 1, 1])
ax.set_facecolor('black')
ax.set_xlim([0, size*2])
ax.set_ylim([0, size*2])
ax.set_zlim([0, size*2])
plt.show()
plot_spheres_in_cube()
def draw_3d_sqr(self):
fig = plt.figure()
fig.patch.set_facecolor('grey') # Background color
ax = fig.add_subplot(111, projection='3d')
# Set the size of the cube
size = 4
r = size / 2
# Define the positions of the sphere centers
centers = [
[r, r, r],
[3 * r, r, r],
[r, 3 * r, r],
[3 * r, 3 * r, r],
[r, r, 3 * r],
[3 * r, r, 3 * r],
[r, 3 * r, 3 * r],
[3 * r, 3 * r, 3 * r]
]
# Plot the spheres
u, v = np.mgrid[0:2 * np.pi:20j, 0:np.pi:10j]
for center in centers:
x = r * np.cos(u) * np.sin(v) + center[0]
y = r * np.sin(u) * np.sin(v) + center[1]
z = r * np.cos(v) + center[2]
ax.plot_surface(x, y, z, color='red', alpha=0.6, edgecolor='none', shade=True)
# Plot the center cube
cube_center = [2 * r, 2 * r, 2 * r]
cube_size = r
cube_vertices = np.array([
[cube_center[0] - cube_size / 2, cube_center[1] - cube_size / 2, cube_center[2] -
cube_size / 2],
[cube_center[0] + cube_size / 2, cube_center[1] - cube_size / 2, cube_center[2] -
cube_size / 2],
[cube_center[0] + cube_size / 2, cube_center[1] + cube_size / 2, cube_center[2] -
cube_size / 2],
[cube_center[0] - cube_size / 2, cube_center[1] + cube_size / 2, cube_center[2] -
cube_size / 2],
[cube_center[0] - cube_size / 2, cube_center[1] - cube_size / 2, cube_center[2] +
cube_size / 2],
[cube_center[0] + cube_size / 2, cube_center[1] - cube_size / 2, cube_center[2] +
cube_size / 2],
[cube_center[0] + cube_size / 2, cube_center[1] + cube_size / 2, cube_center[2] +
cube_size / 2],
[cube_center[0] - cube_size / 2, cube_center[1] + cube_size / 2, cube_center[2] +
cube_size / 2]
])
cube_faces = [
[cube_vertices[j] for j in [0, 1, 5, 4]],
[cube_vertices[j] for j in [7, 6, 2, 3]],
[cube_vertices[j] for j in [0, 3, 7, 4]],
[cube_vertices[j] for j in [1, 2, 6, 5]],
[cube_vertices[j] for j in [0, 1, 2, 3]],
[cube_vertices[j] for j in [4, 5, 6, 7]]
]
ax.add_collection3d(Poly3DCollection(cube_faces, facecolors='black', linewidths=1,
edgecolors='b', alpha=.6))
# Draw the outer cube
outer_cube_range = [0, size * 2]
for s, e in combinations(np.array(list(product(outer_cube_range, outer_cube_range,
outer_cube_range))), 2):
if np.sum(np.abs(s - e)) == outer_cube_range[1] - outer_cube_range[0]:
ax.plot3D(*zip(s, e), color="black")
ax.set_xlim(0, size * 2)
ax.set_ylim(0, size * 2)
ax.set_zlim(0, size * 2)
ax.set_xticks([])
ax.set_yticks([])
ax.set_zticks([])
plt.show()
def run_2d(self):
self.area_calculator_window = tk.Toplevel(self.root)
self.area_calculator_window.title("Area Calculator")
tk.Label(self.area_calculator_window, text="Select the shape:").grid(row=0, column=0,
columnspan=2)
self.shape_var = tk.StringVar(value="circle")
circle_radio = tk.Radiobutton(self.area_calculator_window, text="Circle",
variable=self.shape_var, value="circle")
circle_radio.grid(row=1, column=0, sticky="w")
square_radio = tk.Radiobutton(self.area_calculator_window, text="Square",
variable=self.shape_var, value="square")
square_radio.grid(row=1, column=1, sticky="w")
tk.Label(self.area_calculator_window, text="Radius:").grid(row=2, column=0)
self.radius_entry = tk.Entry(self.area_calculator_window)
self.radius_entry.grid(row=2, column=1)
tk.Label(self.area_calculator_window, text="Side length:").grid(row=3, column=0)
self.side_entry = tk.Entry(self.area_calculator_window)
self.side_entry.grid(row=3, column=1)
calculate_button = tk.Button(self.area_calculator_window, text="Calculate",
command=self.calculate_area)
calculate_button.grid(row=4, column=0, columnspan=2)
self.result_label = tk.Label(self.area_calculator_window, text="")
self.result_label.grid(row=5, column=0, columnspan=2)
def run_3d(self):
self.area_calculator_window = tk.Toplevel(self.root)
self.area_calculator_window.title("Area Calculator")
tk.Label(self.area_calculator_window, text="Select the shape:").grid(row=0, column=0,
columnspan=2)
self.shape_var = tk.StringVar(value="sphere")
circle_radio = tk.Radiobutton(self.area_calculator_window, text="Sphere",
variable=self.shape_var, value="circle")
circle_radio.grid(row=1, column=0, sticky="w")
square_radio = tk.Radiobutton(self.area_calculator_window, text="Cube",
variable=self.shape_var, value="square")
square_radio.grid(row=1, column=1, sticky="w")
tk.Label(self.area_calculator_window, text="Radius:").grid(row=2, column=0)
self.radius_entry = tk.Entry(self.area_calculator_window)
self.radius_entry.grid(row=2, column=1)
tk.Label(self.area_calculator_window, text="Side length:").grid(row=3, column=0)
self.side_entry = tk.Entry(self.area_calculator_window)
self.side_entry.grid(row=3, column=1)
calculate_button = tk.Button(self.area_calculator_window, text="Calculate",
command=self.calculate_area)
calculate_button.grid(row=4, column=0, columnspan=2)
self.result_label = tk.Label(self.area_calculator_window, text="")
self.result_label.grid(row=5, column=0, columnspan=2)
def calculate_area(self):
shape = self.shape_var.get()
try:
if shape == 'circle':
radius = float(self.radius_entry.get())
area = math.pi * radius ** 2
self.result_label.config(text=f"The area of the circle is: {area:.2f}")
elif shape == 'square':
side_length = float(self.side_entry.get())
area = side_length ** 2
self.result_label.config(text=f"The area of the square is: {area:.2f}")
except ValueError:
messagebox.showerror("Invalid input", "Please enter valid numbers.")
# Create the main window
root = tk.Tk()
app = VideoBackgroundApp(root)
root.mainloop()
