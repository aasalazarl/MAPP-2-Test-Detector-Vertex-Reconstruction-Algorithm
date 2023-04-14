# VERTEX GENERATOR

# Import libraries.
import numpy as np
#from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

###########################################
# Boxes dimensions and positions:
# The veto wall is placed at the origin, facing the positive y-direction.
# The boxes are centered at the y axis, with the openings facing the
# negative y-direction.

# Box A: at y = 2.40 w/dimensions 3 x 3 x 3
# Box B: at y = 5.30 w/dimensions (3+2d) x (3+2d) x (3+2d)
# Box C: at y = 5.60 w/dimensions (3+4d) x (3+4d) x (3+4d)

# Veto wall located at y = -2.40

# In the following: S = straight ahead the veto
#                   L = left (negative x-direction)
#                   R = right (positive x-direction)
#                   U = up (positive z-direction)
#                   D = down (negative z-direction)

# 1 refers to track 1; 2 refers to track 2.
#############################################
# Draw the boxes.
import boxDrawer

#boxDrawer

# Plot

figbox = plt.figure()
ax = figbox.add_subplot(1,1,1, projection = '3d')

d = 0.30   

# Box A.
size = 3.00
pos = size/2
zpos = -4.80 + 2.40
clor = 'blue'
boxDrawer.S_planeGenerator(size, pos, size, clor, ax)
boxDrawer.LR_planeGenerator(pos, size, size, -zpos, clor, ax)
boxDrawer.TB_planeGenerator(size, size, pos, -zpos, clor, ax)

# Box B.
size = 3.00 + 2*d
pos = size/2
zpos = -5.30 + 2.40
clor = 'red'
boxDrawer.S_planeGenerator(size, pos, size, clor, ax)
boxDrawer.LR_planeGenerator(pos, size, size, -zpos, clor, ax)
boxDrawer.TB_planeGenerator(size, size, pos, -zpos, clor, ax)

# Box C.
size = 3.00 + 4*d
pos = size/2
zpos = -5.60 + 2.40
clor = 'yellow'
boxDrawer.S_planeGenerator(size, pos, size, clor, ax)
boxDrawer.LR_planeGenerator(pos, size, size, -zpos, clor, ax)
boxDrawer.TB_planeGenerator(size, size, pos, -zpos, clor, ax)
""" Used -zpos for plotting purposes """


# Locate the boxes and set-up parameters and boundaries.
d = 0.30; # i.e., 10 cm.

# Straight ahead:
zA_S = -4.80 + 2.40; zB_S = -5.30 + 2.40; zC_S = -5.60 + 2.40;

# Left and right:
xA_L = -1.50; xA_R = 1.50;
xB_L = -1.50-d; xB_R = 1.50+d;
xC_L = -1.50-2*d; xC_R = 1.50+2*d;

# Up and down:
yA_U = 1.50; yA_D = -1.50;
yB_U = 1.50+d; yB_D = -1.50-d;
yC_U = 1.50+2*d; yC_D = -1.50-2*d;

# Vertex location:
x0 = 0; z0 = 0; y0 = 0;

# Box A.
x1A_S = []; x1A_U = []; x1A_D = []; x1A_L = xA_L;
x2A_S = []; x2A_U = []; x2A_D = []; x2A_R = xA_R;
z1A_L = []; z1A_U = []; z1A_D = []; z1A_S = zA_S;
z2A_R = []; z2A_U = []; z2A_D = []; z2A_S = zA_S;
y1A_S = []; y1A_L = []; y1A_R = []; y1A_U = yA_U; y1A_D = yA_D;
y2A_S = []; y2A_L = []; y2A_R = []; y2A_U = yA_U; y2A_D = yA_D;

# Box B.
x1B_S = []; x1B_U = []; x1B_D = []; x1B_L = xB_L;
x2B_S = []; x2B_U = []; x2B_D = []; x2B_R = xB_R;
z1B_L = []; z1B_U = []; z1B_D = []; z1B_S = zB_S;
z2B_R = []; z2B_U = []; z2B_D = []; z2B_S = zB_S;
y1B_S = []; y1B_L = []; y1B_R = []; y1B_U = yB_U; y1B_D = yB_D;
y2B_S = []; y2B_L = []; y2B_R = []; y2B_U = yB_U; y2B_D = yB_D;

# Box C.
x1C_S = []; x1C_U = []; x1C_D = []; x1C_L = xC_L;
x2C_S = []; x2C_U = []; x2C_D = []; x2C_R = xC_R;
z1C_L = []; z1C_U = []; z1C_D = []; z1C_S = zC_S;
z2C_R = []; z2C_U = []; z2C_D = []; z2C_S = zC_S;
y1C_S = []; y1C_L = []; y1C_R = []; y1C_U = yC_U; y1C_D = yC_D;
y2C_S = []; y2C_L = []; y2C_R = []; y2C_U = yC_U; y2C_D = yC_D;

##############################################
# Real vertices coordinates.
# Use polar coordinates. All units in meters.

rotangle = np.linspace(0 * (np.pi/180), 90 * (np.pi/180), 2) # Angle with respect to positive x-axis.
opangle = 40 * (np.pi/180) # Opening angle from forward motion of initial particle.
opanglediv2 = opangle/2 # Angle from positive y-axis.

#############################################
# Define function for extracting coordinates.

# For the following, look at the derivation document.
def coordinates_S(z_S, theta, phi):
    z1 = z_S
    #z1 = 0
    r1 = z1/np.cos(theta)
    x1 = r1 * np.sin(theta)
    x2 = x1 * np.cos(phi)
    z2 = z1
    y2 = x1 * np.sin(phi)
    return x2, z2, y2
# When calling this function: x1I_S = -x2, x2I_S = x2,
    # z1I_S = -z2, z2I_S = z2, y1I_S = y2, y2I_S = y2.
  
def coordinates_LR(x_l, theta, phi):
    x1 = x_l
    if theta == np.pi/2 and phi == 0:
        x2 = 1.50
        z2 = 0
        y2 = 0
        r1 = 1.50
        r2 = r1
    elif phi == 0:
        x1 = x_l
        x2 = 1.50
        y2 = 0
        r2 = x2 / np.sin(theta)
        z2 = np.sqrt(r2**2 - x2**2 - y2**2)    
        r1 = x1 / np.sin(theta)
        #print('r1, r2', r1, r2)
    elif theta == np.pi/2:
        x2 = 1.50
        z2 = 0
        r2 = x2 / np.cos(phi)
        y2 = r2 * np.sin(phi)
        r1 = x1
        #print('r1, r2', r1, r2)
    else:
        #z1 = 0
        r1 = x1/np.sin(theta)
        z1 = r1 * np.cos(theta)
        h1 = x1 * np.sin(phi)
        h2 = x1 * (1 - np.cos(phi))
        x2 = x1
        t = h2 * (r1/(x1 - h2))
        z2 = z1 * (1 + t/r1)
        y2 = h1 * (1 + t/r1)  
        r2 = np.sqrt(x2**2 + z2**2 + y2**2)
        #print('r1, r2', r1, r2)
    return x2, z2, y2
# When calling this function: z1I_L = -z2, z2I_R = z2,
    # x1I_L = -x2, x2I_R = x2, y1I_L = y2I_R = y2.
# Depending on the incoming angle of the particle, theta
    # is no longer applicable and has to be replaced by two separate angles,
    # one for the left side and one for the right side. The formulas/
    # algorithm remain the same.

def coordinates_TB(y_l, theta, phi):
    phitilde = np.pi/2 - phi
    y1 = y_l
    if theta == np.pi/2 and phitilde == 0:
        y2 = 1.50
        z2 = 0
        x2 = 0
        r1 = 1.50
        r2 = r1
    elif phitilde == 0:
        y1 = y_l
        y2 = 1.50
        x2 = 0
        r2 = y2 / np.sin(theta)
        z2 = np.sqrt(r2**2 - y2**2 - x2**2)    
        r1 = y1 / np.sin(theta)
        #print('r1, r2', r1, r2)
    elif theta == np.pi/2:
        y2 = 1.50
        z2 = 0
        r2 = y2 / np.cos(phitilde)
        x2 = r2 * np.sin(phitilde)
        r1 = y1
        #print('r1, r2', r1, r2)
    else:
        #x1 = 0
        r1 = y1/np.sin(theta)
        z1 = r1 * np.cos(theta)
        h1 = y1 * (1 - np.cos(phitilde))
        h2 = y1 * np.sin(phitilde)
        y2 = y1
        t = h1 * (r1/(y1 - h1))
        z2 = z1 * (1 + t/r1)
        x2 = h2 * (1 + t/r1)  
        r2 = np.sqrt(x2**2 + z2**2 + y2**2)
        #print('r1, r2', r1, r2)
    return x2, z2, y2
    
# When calling this function: z2I_T = x2, z1I_B = -z2,
    # x2I_T = x2, x1I_B = -x2, y2I_T = y1I_B = y2.
# Depending on the incoming angle of the particle, theta
    # is no longer applicable and has to be replaced by two separate angles,
    # one for the left side and one for the right side. The formulas/
    # algorithm remain the same.
    
##########################################
# Generate intersections.
openingangle = 110
theta = openingangle/2 * np.pi/180
phi = 80 * np.pi/180

import boxSelector

# Box A. ---------------------------
x, z, y = coordinates_S(-2.40, theta, phi)
x1S = -x; x2S = x; z1S = z; z2S = z; y1S = -y; y2S = y;
x1S = -x1S; y1S = -y1S;
x2S = -x2S; y2S = -y2S;
#print(x1S, y1S, z1S)

x, z, y = coordinates_LR(1.50, theta, phi)
x1L = -x; x2R = x; z1L = z; z2R = z; y1L = -y; y2R = y;
z1L = -z1L; z2R = -z2R;
#print(x1L, y1L, z1L)

x, z, y = coordinates_TB(1.50, theta, phi)
x1BM = -x; x2T = x; z1BM = z; z2T = z; y1BM = -y; y2T = y;
z1BM = -z1BM; z2T = -z2T;
#print(y1BM)

face = boxSelector.selectorTrack1(x1S, x1L, x1BM, z1S, z1L, z1BM, y1S, y1L, y1BM, 'A', d)

if face == 1:
    x1A = x1S; x2A = x2S; z1A = z1S; z2A = z2S; y1A = y1S; y2A = y2S;
elif face == 2:
    x1A = x1L; x2A = x2R; z1A = z1L; z2A = z2R; y1A = y1L; y2A = y2R;
elif face == 3:
    x1A = x1BM; x2A = x2T; z1A = z1BM; z2A = z2T; y1A = y1BM; y2A = y2T;
# If the vertex and decay are not centered, we need two r's: r1S, r2S, etc.
    
print('x1A, z1A, y1A:', x1A, z1A, y1A)
print('x2A, z2A, y2A:', x2A, z2A, y2A)

#ax.scatter(x1A, y1A, z1A, color = 'blue', label = 'Box A intersection')
#ax.scatter(x2A, y2A, z2A, color = 'blue')
ax.scatter(x1A, -z1A, y1A, color = 'blue', label = 'Box A intersection')
ax.scatter(x2A, -z2A, y2A, color = 'blue') # Negative z's necessary for plotting


# Box B. ----------------------------
x, z, y = coordinates_S(-5.30 + 2.40, theta, phi)
x1S = -x; x2S = x; z1S = z; z2S = z; y1S = -y; y2S = y;
x1S = -x1S; x2S = -x2S;
y1S = -y1S; y2S = -y2S;
#print(x1S, y1S, z1S)

x, z, y = coordinates_LR(1.50 + d, theta, phi)
x1L = -x; x2R = x; z1L = z; z2R = z; y1L = -y; y2R = y;
z1L = -z1L; z2R = -z2R;
#print(x1L, y1L, z1L)

x, z, y = coordinates_TB(1.50 + d, theta, phi)
x1BM = - x; x2T = x; z1BM = z; z2T = z; y1BM = -y; y2T = y;
z1BM = -z1BM; z2T = -z2T;
#print(x1B, y1B, z1B)

face = boxSelector.selectorTrack1(x1S, x1L, x1BM, z1S, z1L, z1BM, y1S, y1L, y1BM, 'B', d)

if face == 1:
    x1B = x1S; x2B = x2S; z1B = z1S; z2B = z2S; y1B = y1S; y2B = y2S;
elif face == 2:
    x1B = x1L; x2B = x2R; z1B = z1L; z2B = z2R; y1B = y1L; y2B = y2R;
elif face == 3:
    x1B = x1BM; x2B = x2T; z1B = z1BM; z2B = z2T; y1B = y1BM; y2B = y2T;

print('x1B, z1B, y1B:', x1B, z1B, y1B)    
print('x2B, z2B, y2B:', x2B, z2B, y2B)

#ax.scatter(x1B, y1B, z1B, color = 'red', label = 'Box B intersection')
#ax.scatter(x2B, y2B, z2B, color = 'red')
ax.scatter(x1B, -z1B, y1B, color = 'red', label = 'Box B intersection')
ax.scatter(x2B, -z2B, y2B, color = 'red')

# Box C. ----------------------------
x, z, y = coordinates_S(-5.60 + 2.40, theta, phi)
x1S = -x; x2S = x; z1S = z; z2S = z; y1S = -y; y2S = y;
x1S = -x1S; x2S = -x2S;
y1S = -y1S; y2S = -y2S;
#print(x1S, y1S, z1S)

x, z, y = coordinates_LR(1.50 + 2*d, theta, phi)
x1L = -x; x2R = x; z1L = z; z2R = z; y1L = -y; y2R = y;
z1L = -z1L; z2R = -z2R;
#print(x1L, y1L, z1L)

x, z, y = coordinates_TB(1.50 + 2*d, theta, phi)
x1BM = - x; x2T = x; z1BM = z; z2T = z; y1BM = -y; y2T = y;
z1BM = -z1BM; z2T = -z2T;
#print(x1B, y1B, z1B)

face = boxSelector.selectorTrack1(x1S, x1L, x1BM, z1S, z1L, z1BM, y1S, y1L, y1BM, 'C', d)

if face == 1:
    x1C = x1S; x2C = x2S; z1C = z1S; z2C = z2S; y1C = y1S; y2C = y2S;
elif face == 2:
    x1C = x1L; x2C = x2R; z1C = z1L; z2C = z2R; y1C = y1L; y2C = y2R;
elif face == 3:
    x1C = x1BM; x2C = x2T; z1C = z1BM; z2C = z2T; y1C = y1BM; y2C = y2T;

print('x1C, z1C, y1C:', x1C, z1C, y1C)    
print('x2C, z2C, y2C:', x2C, z2C, y2C)

#ax.scatter(x1C, y1C, z1C, color = 'orange', label = 'Box C intersection')
#ax.scatter(x2C, y2C, z2C, color = 'orange')
ax.scatter(x1C, -z1C, y1C, color = 'orange', label = 'Box C intersection')
ax.scatter(x2C, -z2C, y2C, color = 'orange')

# Plot the vertex.

ax.scatter(0, 0, 0, color = 'purple')

##################################
# Generate the tracks (vector calculus).
r1C = np.sqrt(x1C**2 + z1C**2 + y1C**2); r2C = np.sqrt(x2C**2 +z2C**2 + y2C**2);
#t1 = np.arange(0, r1C, 0.01); t2 = np.arange(0, r2C, 0.01);
t1 = np.arange(-1, r1C+1, 0.01); t2 = np.arange(-1, r2C+1, 0.01);
xtrack1 = x1C * t1 / r1C; ztrack1 = z1C * t1 / r1C; ytrack1 = y1C * t1 / r1C;
xtrack2 = x2C * t2 / r2C; ztrack2 = z2C * t2 / r2C; ytrack2 = y2C * t2 / r2C;

s1 = 0.01
s2 = 0.01
ax.plot(xtrack1, -ztrack1, ytrack1, '-k', linewidth = 1, label = 'track1')
ax.plot(xtrack2, -ztrack2, ytrack2, '-m', linewidth = 1, label = 'track2')

##################################
# Generate noise.
from numpy import random
def randomGenerator(face, d, length, xythold, zthold):
    #legth = 5
    if face == 'S':
        x = random.rand(length)*2*xythold - xythold;
        z = np.linspace(zthold, zthold, 5)
        y = random.rand(length)*2*xythold - xythold;
    elif face == 'L':
        x = np.linspace(-xythold, -xythold, length);
        z = random.rand(5) * zthold;
        y = random.rand(5)*2*xythold - xythold;
    elif face == 'R':
        x = np.linspace(xythold, xythold, length);
        z = random.rand(5) * zthold;
        y = random.rand(5)*2*xythold - xythold;
    elif face == 'T':
        x = random.rand(5)*2*xythold - xythold;
        z = random.rand(5) * zthold;
        y = np.linspace(xythold, xythold, 5);
    elif face == 'B':
        x = random.rand(5)*2*xythold - xythold;
        z = random.rand(5) * zthold;
        y = np.linspace(-xythold, -xythold, 5);
    return x, z, y

# Box A.
length = 5
xythold = 1.50
zthold = -2.40
xnS, znS, ynS = randomGenerator('S', d, length, xythold, zthold)
xnL, znL, ynL = randomGenerator('L', d, length, xythold, zthold)
xnR, znR, ynR = randomGenerator('R', d, length, xythold, zthold)
xnT, znT, ynT = randomGenerator('T', d, length, xythold, zthold)
xnB, znB, ynB = randomGenerator('B', d, length, xythold, zthold)
ax.scatter(xnS, -znS, ynS, s = 9, color = 'green', label = 'noise')
ax.scatter(xnL, -znL, ynL, s = 9, color = 'green')
ax.scatter(xnR, -znR, ynR, s = 9, color = 'green')
ax.scatter(xnT, -znT, ynT, s = 9, color = 'green')
ax.scatter(xnB, -znB, ynB, s = 9, color = 'green')

# Box B.
length = 5
xythold = 1.50 + d
zthold = -5.30 + 2.40
xnS, znS, ynS = randomGenerator('S', d, length, xythold, zthold)
xnL, znL, ynL = randomGenerator('L', d, length, xythold, zthold)
xnR, znR, ynR = randomGenerator('R', d, length, xythold, zthold)
xnT, znT, ynT = randomGenerator('T', d, length, xythold, zthold)
xnB, znB, ynB = randomGenerator('B', d, length, xythold, zthold)
ax.scatter(xnS, -znS, ynS, s = 9, color = 'green')
ax.scatter(xnL, -znL, ynL, s = 9, color = 'green')
ax.scatter(xnR, -znR, ynR, s = 9, color = 'green')
ax.scatter(xnT, -znT, ynT, s = 9, color = 'green')
ax.scatter(xnB, -znB, ynB, s = 9, color = 'green')


# Box C.
length = 5
xythold = 1.50 + 2*d
zthold = -5.60 + 2.40
xnS, znS, ynS = randomGenerator('S', d, length, xythold, zthold)
xnL, znL, ynL = randomGenerator('L', d, length, xythold, zthold)
xnR, znR, ynR = randomGenerator('R', d, length, xythold, zthold)
xnT, znT, ynT = randomGenerator('T', d, length, xythold, zthold)
xnB, znB, ynB = randomGenerator('B', d, length, xythold, zthold)
ax.scatter(xnS, -znS, ynS, s = 9, color = 'green')
ax.scatter(xnL, -znL, ynL, s = 9, color = 'green')
ax.scatter(xnR, -znR, ynR, s = 9, color = 'green')
ax.scatter(xnT, -znT, ynT, s = 9, color = 'green')
ax.scatter(xnB, -znB, ynB, s = 9, color = 'green')



###################
# Annotate the plot.
ax.legend(loc = 'lower left', bbox_to_anchor=(-0.3, 0.3))
ax.text(-1.50, 2.40 - 3.00, -1.50, 'A')
ax.text(-1.50 - d, 5.30 - 2.40 - 3.00 - 2*d, -1.50 - d, 'B')
ax.text(-1.50 - 2*d, 5.60 - 2.40 - 3.00 - 4*d, - 1.50 - 2*d, 'C')
ax.set_xlabel('x', fontsize = 15); ax.set_ylabel('z', fontsize = 15); 
ax.set_zlabel('y', fontsize = 15);
#ax.set_title('Vertex generation \n from decay intersection with walls', fontsize = 15)
ax.set_title('Vertex reconstruction simulation.png', fontsize = 15)


plt.savefig('Vertex reconstruction simulation.png', dpi = 200, bbox_inches = 'tight')
#plt.savefig('Vertex generation for boxes.png', dpi = 300, bbox_inches = 'tight')

plt.show()

##### SAVE INFORMATION INTO TXT FILE #####

for i in ['x', 'y', 'z']:
    file1 = open(str(i) + '1A.txt', 'w'); 
    if i == 'x':
        file1.write(str(x1A)); file1.close();
    elif i == 'y':
        file1.write(str(y1A)); file1.close();
    elif i == 'z':
        file1.write(str(z1A)); file1.close();
    
    file2 = open(str(i) + '1B.txt', 'w'); 
    if i == 'x':
        file2.write(str(x1B)); file2.close();
    elif i == 'y':
        file2.write(str(y1B)); file2.close();
    elif i == 'z':
        file2.write(str(z1B)); file2.close();
        
    file3 = open(str(i) + '1C.txt', 'w'); 
    if i == 'x':
        file3.write(str(x1C)); file3.close();
    elif i == 'y':
        file3.write(str(y1C)); file3.close();
    elif i == 'z':
        file3.write(str(z1C)); file3.close();
        
    file4 = open(str(i) + '2A.txt', 'w'); 
    if i == 'x':
        file4.write(str(x2A)); file4.close();
    elif i == 'y':
        file4.write(str(y2A)); file4.close();
    elif i == 'z':
        file4.write(str(z2A)); file4.close();
        
    file5 = open(str(i) + '2B.txt', 'w'); 
    if i == 'x':
        file5.write(str(x2B)); file5.close();
    elif i == 'y':
        file5.write(str(y2B)); file5.close();
    elif i == 'z':
        file5.write(str(z2B)); file5.close();
        
    file6 = open(str(i) + '2C.txt', 'w');
    if i == 'x':
        file6.write(str(x2C)); file6.close();
    elif i == 'y':
        file6.write(str(y2C)); file6.close();
    elif i == 'z':
        file6.write(str(z2C)); file6.close(); 
