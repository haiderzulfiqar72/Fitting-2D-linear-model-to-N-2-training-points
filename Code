import matplotlib.pyplot as plt
import numpy as np
import cv2

# Linear solver to fit a line to given data points
def line_fit(x, y):

    n = np.size(x)
    a = (((sum(x*y)) - (sum(x)*sum(y))/n)) / (sum(x**2) - ((sum(x)**2)/n))
    b = np.mean(y) - a*np.mean(x)
   
    return a, b

# Function to plot the regression line and data points
def regression_plot(x_coord, y_coord, reg_line): 
    
    plt.scatter(x_coord, y_coord, color="blue", marker="o", s=10)
    y_output = reg_line[0] * x_coord + reg_line[1]
    plt.plot(x_coord, y_output, color="red")
    plt.xlabel('x')
    plt.ylabel('y')
    plt.title('Regression Analysis')
    plt.show()
    
# Main function for regression analysis
def regression_analysis():

    # Generate random coordinates
    x_coord = np.random.uniform(-1, 3, 10)
    y_coord = np.random.uniform(0, 3, 10)
    
    # Fit a line to the coordinates
    reg_line = line_fit(x_coord, y_coord)

    # Print the slope and intercept of the line
    print("Slope (a) = {}\nIntercept (b) = {}".format(reg_line[0], reg_line[1]))
    print("My fit: a = {} and b = {}".format(reg_line[0], reg_line[1]))
    
    # Plot the regression line and data points
    regression_plot(x_coord, y_coord, reg_line)

# Function to handle mouse click events and plot the line
def mouse_click(event, x_1, y_1, flags, params):

    global x_click_coord, y_click_coord

    if event == cv2.EVENT_LBUTTONUP:
        
        # Store the clicked coordinates
        x_click_coord = np.append(x_click_coord, round(1/50 * (x_1-361), 2))
        y_click_coord = np.append(y_click_coord, round(-1/50 * (y_1-401), 2))
          
    if event == cv2.EVENT_RBUTTONUP:
        # Print the clicked coordinates and plot them
        print('Clicked coordinates: (', x_click_coord, '', y_click_coord, ')')
        plt.plot(x_click_coord, y_click_coord, 'bo')
        
        # Fit a line to the clicked coordinates
        reg_line = line_fit(x_click_coord, y_click_coord)
        
        # Plot the regression line and clicked points
        regression_plot(x_click_coord, y_click_coord, reg_line)
        
        # Print the slope and intercept of the line
        print("Slope (a) = {}\nIntercept (b) = {}".format(reg_line[0], reg_line[1]))
        print("My fit: a = {} and b = {}".format(reg_line[0], reg_line[1]))
    
if __name__ == '__main__':
    
    ## Random sets of points
    # Uncomment the following line to perform regression analysis on random points
    # regression_analysis()

    # Reading the image file
    img = r'E:\Study Material\Tampere - Grad\Studies\Year I\Period I\Introduction to Pattern Recognition and Machine Learning - DATA.ML.100\Excercises\Excercise Week 2\coordinates.jpg'
    image = cv2.imread(img)
    cv2.imshow('coordinates', image)

    x_click_coord = []
    y_click_coord = []
    
    # Set the mouse callback function
    cv2.setMouseCallback('coordinates', mouse_click)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
