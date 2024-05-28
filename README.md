import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Ukuran kolam
diameter_kecil = 4
diameter_besar = 20

# Jarak antara patung kuda
jarak_antar_patung = 17

# Posisi pusat kolam besar (asumsi titik pusat di (0,0))
center_besar = (0, 0)

# Posisi pusat kolam kecil (17 meter ke kanan dari pusat kolam besar)
center_kecil = (jarak_antar_patung, 0)

# Buat plot
fig, ax = plt.subplots()

# Tambahkan kolam besar
kolam_besar = patches.Circle(center_besar, diameter_besar / 2, edgecolor='blue', facecolor='none', lw=2)
ax.add_patch(kolam_besar)

# Tambahkan kolam kecil
kolam_kecil = patches.Circle(center_kecil, diameter_kecil / 2, edgecolor='green', facecolor='none', lw=2)
ax.add_patch(kolam_kecil)

# Tambahkan pagar
# Asumsi pagar menyentuh bagian atas, kiri, dan bawah kolam besar, serta bagian kanan kolam kecil
left = -diameter_besar / 2
right = center_kecil[0] + diameter_kecil / 2
bottom = -diameter_besar / 2
top = diameter_besar / 2
ax.plot([left, right], [top, top], color='black')  # Atas
ax.plot([left, right], [bottom, bottom], color='black')  # Bawah
ax.plot([left, left], [bottom, top], color='black')  # Kiri
ax.plot([right, right], [bottom, top], color='black')  # Kanan

# Tambahkan patung kuda (titik tengah kolam)
ax.plot(*center_besar, marker='o', color='red', markersize=10)  # Patung kuda di kolam besar
ax.plot(*center_kecil, marker='o', color='red', markersize=10)  # Patung kuda di kolam kecil

# Pengaturan plot
ax.set_aspect('equal', 'box')
ax.set_xlim(left - 2, right + 2)
ax.set_ylim(bottom - 2, top + 2)
ax.set_xlabel('Meter')
ax.set_ylabel('Meter')
plt.title('Desain Taman Kota')
plt.grid(True)
plt.show()
