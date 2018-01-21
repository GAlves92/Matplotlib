# Matplotlib-Homework{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "import matplotlib.pyplot as plt\n",
    "import pandas as pd\n",
    "import numpy as np\n",
    "import os"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Observations:\n",
    "\n",
    "1 - The data confirms that the number of drivers in the urban area is significantly higher compared with suburban and rural areas. \n",
    "\n",
    "2 - The average fare rates has followed that same trend, which can suggest other important variable that might be important to consider such as the millennials' lifestyle. They have had an huge impact on urban activities, considering services such as Uber and Lift that are on the top of their list as a ride home option. \n",
    "\n",
    "3- Another important variable is the number of establishments’ such as bars, clubs, dinners, and restaurants which are primarily located at urban areas; therefore, services like Uber and Lyft tend to be more requested mainly around these establishments.    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "cities_data = os.path.join(\"city_data.csv\")\n",
    "ride_data = os.path.join(\"ride_data.csv\")\n",
    "cities_data_df = pd.read_csv(cities_data)\n",
    "ride_data_df = pd.read_csv(ride_data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>city</th>\n",
       "      <th>driver_count</th>\n",
       "      <th>type</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Kelseyland</td>\n",
       "      <td>63</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Nguyenbury</td>\n",
       "      <td>8</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>East Douglas</td>\n",
       "      <td>12</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>West Dawnfurt</td>\n",
       "      <td>34</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Rodriguezburgh</td>\n",
       "      <td>52</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "             city  driver_count   type\n",
       "0      Kelseyland            63  Urban\n",
       "1      Nguyenbury             8  Urban\n",
       "2    East Douglas            12  Urban\n",
       "3   West Dawnfurt            34  Urban\n",
       "4  Rodriguezburgh            52  Urban"
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "cities_data_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(125,)"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "total_cities = cities_data_df.city.value_counts()\n",
    "total_cities.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>city</th>\n",
       "      <th>date</th>\n",
       "      <th>fare</th>\n",
       "      <th>ride_id</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Sarabury</td>\n",
       "      <td>2016-01-16 13:49:27</td>\n",
       "      <td>38.35</td>\n",
       "      <td>5403689035038</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>South Roy</td>\n",
       "      <td>2016-01-02 18:42:34</td>\n",
       "      <td>17.49</td>\n",
       "      <td>4036272335942</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Wiseborough</td>\n",
       "      <td>2016-01-21 17:35:29</td>\n",
       "      <td>44.18</td>\n",
       "      <td>3645042422587</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Spencertown</td>\n",
       "      <td>2016-07-31 14:53:22</td>\n",
       "      <td>6.87</td>\n",
       "      <td>2242596575892</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Nguyenbury</td>\n",
       "      <td>2016-07-09 04:42:44</td>\n",
       "      <td>6.28</td>\n",
       "      <td>1543057793673</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "          city                 date   fare        ride_id\n",
       "0     Sarabury  2016-01-16 13:49:27  38.35  5403689035038\n",
       "1    South Roy  2016-01-02 18:42:34  17.49  4036272335942\n",
       "2  Wiseborough  2016-01-21 17:35:29  44.18  3645042422587\n",
       "3  Spencertown  2016-07-31 14:53:22   6.87  2242596575892\n",
       "4   Nguyenbury  2016-07-09 04:42:44   6.28  1543057793673"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_data_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "63651.30999999986"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_data_df.fare.sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(125,)"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "total_cities = ride_data_df.city.value_counts()\n",
    "total_cities.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "total_cities = ride_data_df.groupby('city').fare.count()\n",
    "#total_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "total_date = ride_data_df.groupby('city').date.value_counts()\n",
    "#total_date"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [],
   "source": [
    "#average_fare = ride_data_df.groupby(\"city\").fare.mean()\n",
    "average_fare = ride_data_df.groupby(\"city\").fare.sum()\n",
    "#average_fare = average_sum.mean() \n",
    "average_fare = average_fare.to_frame().reset_index()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "average_driver_count = cities_data_df.groupby(\"city\").driver_count.mean()\n",
    "average_driver_count = average_driver_count.to_frame().reset_index()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "total_rides = ride_data_df.groupby(\"city\").ride_id.count()\n",
    "total_rides = total_rides.to_frame().reset_index()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "total_drivers = cities_data_df.groupby(\"city\").driver_count.value_counts()\n",
    "#total_drivers"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "cities_category = cities_data_df.groupby(\"city\").type.max()\n",
    "cities_category = cities_category.to_frame().reset_index()\n",
    "#cities_category"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>city</th>\n",
       "      <th>fare</th>\n",
       "      <th>ride_id</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Alvarezhaven</td>\n",
       "      <td>741.79</td>\n",
       "      <td>31</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Alyssaberg</td>\n",
       "      <td>535.85</td>\n",
       "      <td>26</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Anitamouth</td>\n",
       "      <td>335.84</td>\n",
       "      <td>9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Antoniomouth</td>\n",
       "      <td>519.75</td>\n",
       "      <td>22</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aprilchester</td>\n",
       "      <td>417.65</td>\n",
       "      <td>19</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           city    fare  ride_id\n",
       "0  Alvarezhaven  741.79       31\n",
       "1    Alyssaberg  535.85       26\n",
       "2    Anitamouth  335.84        9\n",
       "3  Antoniomouth  519.75       22\n",
       "4  Aprilchester  417.65       19"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_sharing = pd.merge(average_fare, total_rides, on='city', how='left')\n",
    "ride_sharing.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>city</th>\n",
       "      <th>fare</th>\n",
       "      <th>ride_id</th>\n",
       "      <th>driver_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Alvarezhaven</td>\n",
       "      <td>741.79</td>\n",
       "      <td>31</td>\n",
       "      <td>21</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Alyssaberg</td>\n",
       "      <td>535.85</td>\n",
       "      <td>26</td>\n",
       "      <td>67</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Anitamouth</td>\n",
       "      <td>335.84</td>\n",
       "      <td>9</td>\n",
       "      <td>16</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Antoniomouth</td>\n",
       "      <td>519.75</td>\n",
       "      <td>22</td>\n",
       "      <td>21</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aprilchester</td>\n",
       "      <td>417.65</td>\n",
       "      <td>19</td>\n",
       "      <td>49</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           city    fare  ride_id  driver_count\n",
       "0  Alvarezhaven  741.79       31            21\n",
       "1    Alyssaberg  535.85       26            67\n",
       "2    Anitamouth  335.84        9            16\n",
       "3  Antoniomouth  519.75       22            21\n",
       "4  Aprilchester  417.65       19            49"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_sharing = pd.merge(ride_sharing, average_driver_count, on='city', how='left')\n",
    "ride_sharing.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>city</th>\n",
       "      <th>fare</th>\n",
       "      <th>ride_id</th>\n",
       "      <th>driver_count</th>\n",
       "      <th>type</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Alvarezhaven</td>\n",
       "      <td>741.79</td>\n",
       "      <td>31</td>\n",
       "      <td>21</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Alyssaberg</td>\n",
       "      <td>535.85</td>\n",
       "      <td>26</td>\n",
       "      <td>67</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Anitamouth</td>\n",
       "      <td>335.84</td>\n",
       "      <td>9</td>\n",
       "      <td>16</td>\n",
       "      <td>Suburban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Antoniomouth</td>\n",
       "      <td>519.75</td>\n",
       "      <td>22</td>\n",
       "      <td>21</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aprilchester</td>\n",
       "      <td>417.65</td>\n",
       "      <td>19</td>\n",
       "      <td>49</td>\n",
       "      <td>Urban</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           city    fare  ride_id  driver_count      type\n",
       "0  Alvarezhaven  741.79       31            21     Urban\n",
       "1    Alyssaberg  535.85       26            67     Urban\n",
       "2    Anitamouth  335.84        9            16  Suburban\n",
       "3  Antoniomouth  519.75       22            21     Urban\n",
       "4  Aprilchester  417.65       19            49     Urban"
      ]
     },
     "execution_count": 17,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_sharing = pd.merge(ride_sharing, cities_category, on='city', how='left')\n",
    "ride_sharing.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "63651.30999999986"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#ride_sharing.reset_index(inplace=True)\n",
    "#ride_sharing.head()\n",
    "ride_data_df.fare.sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "63651.310000000005"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_sharing.fare.sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "type\n",
       "Rural        4255.09\n",
       "Suburban    19317.88\n",
       "Urban       40078.34\n",
       "Name: fare, dtype: float64"
      ]
     },
     "execution_count": 20,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ride_sharing.groupby('type').fare.sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [],
   "source": [
    "#average_fare = len(average_fare / 125)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "ride_sharing = ride_sharing.set_index(\"city\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [],
   "source": [
    "#ride_sharing.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {},
   "outputs": [],
   "source": [
    "#ride_sharing_numbers = ride_sharing.replace({'Urban': 1, 'Suburban': 2, 'Rural': 3})\n",
    "#ride_sharing_numbers\n",
    "#ride_sharing_numbers.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [],
   "source": [
    "#ride_sharing_numbers.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {},
   "outputs": [],
   "source": [
    "urban_cities = ride_sharing[(ride_sharing.type == \"Urban\")]\n",
    "suburban_cities = ride_sharing[(ride_sharing.type == \"Suburban\")]\n",
    "rural_cities = ride_sharing[(ride_sharing.type == \"Rural\")]\n",
    "#urban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "metadata": {},
   "outputs": [],
   "source": [
    "#urban_cities.count()\n",
    "#suburban_cities.count()\n",
    "#rural_cities.count()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "%matplotlib inline"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAloAAAHsCAYAAAAKIAMfAAAABHNCSVQICAgIfAhkiAAAAAlwSFlz\nAAALEgAACxIB0t1+/AAAIABJREFUeJzs3Xd4lFXe//H3TJJJMum9EUogJAEpgdA7QZQOoui6sgrq\nPqjo2h8rrjy6/FxZu6uyKrrq2qWICNIF6RA6gVBDQkgC6b3N7w+W0QghGcgkIXxe1+V1kbt+54jx\nM+ec+9wGi8ViQURERETqnbGxCxARERFprhS0REREROxEQUtERETEThS0REREROxEQUtERETEThS0\nREREROxEQUvkCvbEE0/w6quvNtr93333XZ5++uka9w8dOpT169fX+30nT57M119/XW/XmzFjBm+/\n/Xa9XU9E5BzHxi5ARM4GktOnT+Pg4ICrqyuDBg3imWeewc3NrVHrmjx5Mjt27MDR0RGTyUSPHj2Y\nMWMGgYGBAEybNs1u93733Xf56quvyM7OxsPDg27duvHaa6/Z5V4zZ860y3VTUlKIj4/HbDYD4Orq\nSqdOnfjTn/5Ev3796nSN7777jq+//prPP//8kmrYsWMHr7/+Onv37sVoNNKzZ0+eeeYZ679Di8XC\n7Nmz+eabbwCYOHEijz32GAaDAYBnn32WzZs3c/z4cf72t79xww03VLv+iRMneOGFF9i8eTMmk4mJ\nEyfy+OOPX1KtIs2RerREmoh3332XhIQE5s2bx+7du3nnnXca9P6VlZUX3D5jxgwSEhJYtmwZRUVF\nvPTSS3avZd68eSxYsICPPvqIhIQEvv32W/r06WOXe9X0uevTli1bSEhIYMGCBfTt25fp06fz3Xff\n2f2+ALm5uUyaNImVK1eyatUq3NzcePLJJ637v/zyS5YvX86CBQtYuHAhq1ev5osvvrDuj46O5q9/\n/SsdOnQ479plZWVMmTKF3r1788svv/Dzzz8zduzYBvlcIlcKBS2RJiYoKIgBAwaQlJTEjz/+eF4P\nwocffsi9995r/Tk7O5spU6YQGxvLbbfdRmpqqnXf4cOHmTJlCj179uS6665j8eLF1n1PPPEEzz33\nHHfffTddu3Zl06ZNF63L09OT+Ph4EhMTrdvefPNNHn30UevP8+fPZ8iQIfTq1eu8oFhVVcWcOXMY\nNmwYvXr14i9/+Qs5OTkXvNfu3bvp378/LVu2BCAgIICbb7652jGpqanccsstxMbGMnXqVLKysqz7\nHnjgAfr160f37t354x//SFJS0kU/92+HYDdt2sTAgQP58MMP6dOnD/379+fbb7+t1t7Tpk2jW7du\nTJw4kVdffZU//OEPF227cwICArj99tuZPn06s2fPpqqqCsDaLrGxsYwcOZJly5YBZ//9Pffcc+zY\nsYPY2Fji4uIAWL16NePHj6dbt24MGjSIN998s8Z7Dho0iBEjRuDu7o6rqyu33XYb27dvt+6fP38+\nU6dOJTg4mKCgIKZMmcK8efOs+//4xz/Sp08fnJ2dz7v2vHnzCAwMZMqUKZjNZpydnYmOjq5TW4hc\nLRS0RJqYtLQ0fv75Z2JiYoiPjyclJYXDhw9b9y9cuJBx48ZZf/7++++599572bRpE9HR0dbgU1RU\nxNSpUxk9ejTr16/nlVde4fnnn68WOhYtWsS0adPYvn073bt3v2hd2dnZLFu2zBp+fu/QoUM8//zz\n/P3vf2ft2rXk5ORw6tQp6/5///vfLF++nE8//ZS1a9fi5eVV45Bdly5dWLBgAe+//z67d+++YK/T\nokWLmDVrFhs2bKC8vJwPP/zQum/gwIEsXbqUDRs20KFDh2phsC6f+/Tp0+Tn5/Pzzz/z4osvMnPm\nTHJzc4Gzw4yurq788ssvvPTSS8yfP/+i7XYhw4cP58yZMxw9ehSA8PBwPvvsM7Zt28b06dN57LHH\nyMjIoG3btjz//PN07dqVhIQEtm7dCpwdgnzppZfYunUr7733Hp9//jnLly+v0723bNlCZGSk9eek\npKRq4Sg6Orra35GL2bFjB2FhYdx111306tWLyZMnc+DAgbo2g8hVQUFLpIm47777iIuL49Zbb6VH\njx5MmzYNk8nEiBEjWLhwIXD2f4qpqakMGTLEet7gwYPp0aMHJpOJhx56iB07dpCWlsbq1asJCwtj\n4sSJODo60rFjR6677jqWLl1qPTc+Pp7u3btjNBov2GMB8MILL9C9e3d69+5NdnY2zz777AWPW7Jk\nSbVa/vKXv2A0/vor5ssvv+Shhx4iODgYk8nE9OnTWbp0KRUVFedda9y4cTzzzDOsW7eOyZMn07dv\nX+bMmVPtmBtuuIE2bdrg4uLC9ddfz/79+637brzxRtzd3TGZTNx///0kJiaSn59f58/t6OjIfffd\nh5OTE4MGDcJsNnP06FEqKyv56aefuP/++3F1daVdu3aMHz/+gu1xMefmR53r0RsxYgRBQUEYjUZG\njhxJq1at2LVrV43n9+rVi6ioKIxGI9HR0YwaNYrNmzfXet/ExET++c9/VptDVVRUhLu7u/VnDw8P\nioqKqMtrcNPT01m8eDGTJ09m7dq1DBo0iHvvvZeysrJazxW5WmgyvEgT8fbbb9O3b9/ztk+YMIGH\nH36YBx98kAULFjBixAhMJpN1f3BwsPXPbm5ueHl5kZGRQWpqKrt27bION8HZ+Ui/nUMTEhJSa13P\nPPMMN910EwcOHGDatGmcOnWK0NDQ847LyMioVovZbMbb29v688mTJ7nvvvuqhS+j0ciZM2cICgo6\n73pjx45l7NixlJeXs3z5ch577DFiYmIYMGAAcHYY7hxXV1eKioqsn/HVV19lyZIlZGVlWe93blJ9\nXT63t7c3jo6//no8d/2srCwqKiqqnV+XNvy99PR0633g7PDd3LlzrcO+RUVFZGdn13j+zp07mT17\nNklJSZSXl1NWVsb1119/0XseP36cu+++m6eeeqra3wmz2UxhYaH154KCAsxms3Uy/MU4Oztbhy8B\n7rzzTt555x2OHDmiIUSR/1LQEmniunbtipOTE1u3bmXRokXMnj272v7fDs8VFhaSm5tLYGAgISEh\n9OjRg7lz59ZLHVFRUdxzzz3MnDmTefPmnfc/4sDAwGpDnMXFxdXmYAUHB/O3v/2t1iHK33NycmLE\niBH861//IikpyRq0avL999+zYsUK5s6dS4sWLcjPz6dHjx516qGpja+vL46Ojpw6dYo2bdoAZ4d6\nbbVs2TL8/Pxo06YNqampPPPMM3z00UfExsbi4OBQbWj4QoHnkUce4bbbbuP999/H2dmZF1988aLB\nLDU1lSlTpnDvvfee1wMXGRlJYmIinTt3Bs72ev12aPFioqKiqs33EpHzaehQ5Aowfvx4Zs6ciYOD\nQ7XeCIA1a9awdetWysrKeP311+nSpQshISEMHjyYY8eOMX/+fMrLyykvL2fXrl3VwtCl1HHmzBlW\nrFhx3r7rrruO1atXW2t54403rJO9Af7whz/w2muvWXttsrKyapxX9N1337F69WoKCgqoqqpizZo1\nHDp0yBoGLqawsBCTyYSPjw/FxcW88sorl/hpz+fg4MC1117LW2+9RXFxMYcPH2bBggV1Pv/06dN8\n+umnvPXWWzz88MMYjUaKi4sxGAz4+voC8O2331abI+Xn50d6enq14bjCwkK8vLxwdnZm165dLFq0\n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\nk2nTplonwwP88Y9/4oUX/sqXX35Gt249LunziIiIiH01yMrwtrqcBUutTx2260yrdtE4Ojmdferw\nUCKZh3Zd1lOHzYkW+rOd2sw2ai/bqc1so/ayndrMNvWxYGmz6tEC8PLyZsLI69m8bRvrFyXg5GKm\nvKSINmHBClkiIiLSoJpd0IKzYevaofGUlJRQXHx2TtbVOjYsIiIijadZBq1zXFxcFLBERESk0TSr\npw5FREREmhIFLRERERE7UdASERERsZNmPUervg0c2JOIiHZUVlYQEhLGs8/OxMOj5kc6bfHBB+/h\n6mrm1lsn18v1REREpPGpR8sGzs7OfPTRf/jkk6/w9PTku+++sun8yspKO1UmIiIiTVGz7dE6c+YM\ne3dvJCf7BN4+4XTs1Bs/P796u/4113Ti0KFDAGzfvpUvvviUv//9NQBeeeUloqM7MHLkGG68cQyj\nRo1l8+aNTJw4iaKiIhYunEd5eTktWrTg2Wf/T09GioiINFPNMmidOXOGVT/9i+4dqoiL9iQ9fSer\nftrNkOF310vYqqysZOvWLYwePa5Ox5tMJt555wMAcnNzGDt2AgBz5vyTRYvmc+ONt1x2TSIiItL0\nNMugtXf3Rrp3qCImKgQAX283II29uzcycPCoS75uaWkpd9xxK6dOnSQqKoYePXrV6bz4+OHWPx85\ncph//esdCgryKS4upmfP3pdcj4iIiDRtzXKOVk72CYKCPKttCwryJCf7xGVd99wcrW++WUR5eTnf\nffc1AA4OjlRVVVmPKysrq3aei4ur9c9/+9vzPPTQ4/z7318yZcrd5x0rIiIizUezDFrePuGkp+dV\n25aenoe3T3i9XN/d3Z0HH3yUzz//hIqKCoKDgzl27ChlZWUUFBSwbduWGs8tKirE39+fiooKfvrp\nx3qpR0RERJqmZjl02LFTb1b9tBtIIyjIk/T0PLbtMzJkeP0N07VvH027du1Zvnwp118/iqFDh3H7\n7bcQHt6SyMioGs+76657+POf7yAoKJi2bdtRVKS3qIuIiDRXBovFYmnsIn4vMzPf5nO8vc3k5Pwa\nWuz91OGV7vftJbVTm9lG7WU7tZlt1F62U5vZpq7tFRBQ85qazbJHC8DPz++yJr6LiIiIXK5mOUdL\nREREpClQ0BIRERGxEwUtERERETtR0BIRERGxEwUtERERETtR0BIRERGxEwUtERERETtR0BIRERGx\n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\nuugxpcVFODs7N1BFIk2fgpaIiNRJaGgYZXlnKMzPu+D+iooKslIO07p164YtTKQJU9ASEZE6cXR0\nJK5TR3ZtWElpaUm1fZWVlezauJroli3w8PBspApFmh4t7yAiInXWuVNnysvL2fzj1/i0iMDN04eS\nokIykw8S2SKEfn37NnaJIk2KgpaIiNike7fuREdFc+TIYfIKswhyc2boqOvx8vJu7NJEmhwFLRER\nsZmbmxudOnVu7DJEmjzN0RIRERGxEwUtERERETtR0BIRERGxEwUtERERETtR0BIRERGxEwUtERER\nETtR0BIRERGxEwUtERERETtR0BIRERGxEwUtERERETtR0BIRERGxEwUtERERETtR0BIRERGxEwUt\nERERETtR0BIRERGxE8fGLkBERK4+GRkZrFq3DlcXF64dMgRXV9fGLknELtSjJSIiDW77rp14tOpA\ngaM7hw8fauxyROxGQUtERBpccEAAaYf3UZiZir+/f2OXI2I3GjoUEZEG17VLV4KDgnB2dsbHx7ex\nyxGxGwUtERFpFMHBIY1dgojdaehQRERExE4UtERERETsREFLRERExE4UtERERETsREFLRERExE4U\ntERERETsREFLRERExE4UtERERETsREFLRERExE4UtERERETsREFLRERExE4UtERERETsREFLRERE\nxE4UtERERETspNagVVxczNtvv80zzzwDwLFjx1i1apXdCxMRERG50tUatJ588klMJhM7duwAIDg4\nmNdee83uhYmIiIhc6WoNWsnJydx99904OjoC4OLigsVisXthIiIiIle6WoOWyWSipKQEg8EAnA1e\nJpPJ7oWJiIiIXOkcazvg/vvv56677iItLY1HHnmEhIQEZs2a1RC1iYiIiFzRLhq0LBYLERERvPnm\nm+zcuROLxcLTTz+Nr69vQ9UnIiIicsW6aNAyGAzcd999fPfddwwePLiBShIRERFpHmqdo9WlSxd2\n7drVELWI2FVVVVVjlyAiIleZWudobdq0iS+//JLQ0FBcXV2t27///nu7FiZSHyorK9m9azuHD66n\npCQXN/cAomIGEB3T0fqAh4iIiL3UGrT+9a9/NUQdIvXOYrGwZtUiTFXbGTU4EG+vcDJP57Nx+1fk\n5cfTq9egxi5RRESauVqHDsPCwggLC8PFxQWDwWD9R6SpO3UqjZK8BIb2b4m3lxmAAH8PrhsczonD\n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\nP4ZKUmviYJAFAAAAAElFTkSuQmCC\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x1f2dc9d8240>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "color = ['red', 'lightskyblue', 'gold']\n",
    "\n",
    "with plt.style.context(\"seaborn-darkgrid\"):\n",
    "    plt.figure(figsize=(10,8))\n",
    "    urban = plt.scatter(x=urban_cities[\"ride_id\"], y=urban_cities[\"fare\"] / 66,\n",
    "    s=urban_cities[\"driver_count\"] * 5, color=color[0], marker='o', alpha=.4, edgecolor= 'black', linewidths=1.0)\n",
    "    suburban = plt.scatter(x=suburban_cities[\"ride_id\"], y=suburban_cities[\"fare\"] / 41,\n",
    "    s=suburban_cities[\"driver_count\"] * 5, color=color[1], marker='o', alpha=.4, edgecolor= 'black', linewidths=1.0)\n",
    "    rural = plt.scatter(x=rural_cities[\"ride_id\"], y=rural_cities[\"fare\"] / 18,\n",
    "    s=rural_cities[\"driver_count\"] * 5, color=color[2], marker='o', alpha=.4, edgecolor= 'black', linewidths=1.0)\n",
    "    plt.title(\"Pyber Ride Sharing Data 2016\")\n",
    "    plt.ylabel(\"($) Average Fare\")\n",
    "    plt.xlabel(\"Total Number of Rides (Per City)\")\n",
    "    plt.legend((urban, suburban, rural),\n",
    "           ('Urban', 'Suburban', 'Rural'),\n",
    "           scatterpoints=1,\n",
    "           loc='best',\n",
    "           ncol=1,\n",
    "           fontsize=10,\n",
    "           title=\"City Types\")\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "63651.310000000005"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Total Fares By City type\n",
    "#len(ride_sharing)\n",
    "fare_ride_sharing = ride_sharing.fare.sum()\n",
    "fare_ride_sharing"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[62.96545978393845]"
      ]
     },
     "execution_count": 31,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "urban_cities = ride_sharing[(ride_sharing.type == \"Urban\")]\n",
    "#len(urban_cities)\n",
    "fare_urban_cities = urban_cities.fare.sum()\n",
    "#fare_urban_cities\n",
    "per_urban_cities = [((fare_urban_cities) / (fare_ride_sharing)) * 100]\n",
    "per_urban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[30.349540331534413]"
      ]
     },
     "execution_count": 32,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "suburban_cities = ride_sharing[(ride_sharing.type == \"Suburban\")]\n",
    "#len(suburban_cities)\n",
    "fare_suburban_cities = suburban_cities.fare.sum()\n",
    "#fare_suburban_cities\n",
    "per_suburban_cities = [((fare_suburban_cities) / (fare_ride_sharing)) * 100]\n",
    "per_suburban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[6.684999884527121]"
      ]
     },
     "execution_count": 33,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rural_cities = ride_sharing[(ride_sharing.type == \"Rural\")]\n",
    "#len(rural_cities)\n",
    "fare_rural_cities = rural_cities.fare.sum()\n",
    "#fare_rural_cities\n",
    "per_rural_cities = [((fare_rural_cities) / (fare_ride_sharing)) * 100]\n",
    "per_rural_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAWQAAAD7CAYAAABdXO4CAAAABHNCSVQICAgIfAhkiAAAAAlwSFlz\nAAALEgAACxIB0t1+/AAAIABJREFUeJzt3Xl8VNX5x/HPM1nJNgES9k0WJwRQNlEKFRD1ZzR1t251\nqVpr3Wtra1vtmLrUWmvVqtUurlW0dlGMgiJLlCqgsmpIQGQnLCGQBLIn5/fHucEhJCGEJHdm8rxf\nr3mR3Jm580yAb86cexYxxqCUUsp9HrcLUEopZWkgK6VUkNBAVkqpIKGBrJRSQUIDWSmlgoQGslJK\nBQkN5DAhIveLSKGIbHe5jhtE5AM3azgSIpIpInkd9FpniMjnHfFaKjRpIHcgEXlMRPaIyCci0jfg\n+OUi8vhRnLc/8BMg3RjTq8F9l4vIPudWLiJ1Ad/va8G5XxORu1tbW4NzpYmICXx9EVnSFucOFiIy\nWUTmiEiJiOx2/q4vBTDGzDbGjAt4bKGInNSK1zgj4OdX1sjPtHtbvifVcTSQO4iITADGAb2AhcAv\nnONe4KfAr4/i9AOB3caYnQ3vMMa8YoxJMMYkABnAtvrvnWMdrTbw9Y0xE470BCIS2R6FHS0RmQ7M\nBt4BBgEpwI+BzLZ8HSfY6//+JgCVDX6mu9vy9VTH0UDuOMcAC40xlcBcYLBz/AHg98aY4uaeLCJe\nEXlJRHaJyEYRuVtEPCJyKjAH6OO0jl440sJEZJSIfCQie0VkpYhkOMdvBS4A7nHO/YZz/Ncisl5E\nSkXkCxE560hfs5Ea0kXkQxEpEpGdIvK8iCQE3F8oIneISC5Q5BwbKCJvO/etE5EfBDz+2yKy3Gmp\nFojI/Yd5/fud1/5aRM53jk0TkQ0iIgGPu0pEFjZxmj8ATxljHjPGFBlrkTHmcue5B7pHROS/QHdg\nnvOzvVFEckTk+w3qWuf8HbeYiPxAROY2OHZf/b8NEXlTRP7o/J2XiMh7ItIr4LGjnVr2iMiXbfH3\nq1rIGKO3DrgBI7Et4y7A753beGBOC5//EvAWkIhtfa0BrnXumwpsacE5DnkcEAtsxHZ5RAH/B+wD\njnHufw24u8FzLgZ6Y3+hXwGUAinOfTcAHzTx+mlATRP3pTv1RTnnXgLcH3B/IbDIua8LEAnkBtSd\nBmwBJjuPXwWc53ydBExo4nUzgRrgfiDaef9lwABAgA3AtwMePwf4YSPnSQEMcEIzP/9MIK/Bezop\n4PtrgLkB308CtgKew/y7qmhwzOv8HfYNOPY1MN35+k1gN3CC87N8Hsh27usG7AAuAiKAb2F/AQ50\n+/9QZ7hpC7mDGGO+AP6NDZUBwO+Ax4FbReRWp3X4iogkN3yuiERgQ/AXxphSY8wGbGvsijYo7dvO\nn48aY6qNMe9hQ+fiZt7L68aYAmNMnTHmZWxojGvq8Q1EOC3x+tvNzjlzjTELnBoKgCeAKQ2e+6jz\nuuXOfWKM+YPznDzgxYC6q4FjRaSbMabEGNNcX3Ul8BtjTJXz/hcAFxibUC8D3wMQkT7YkPxnI+eo\n77ctaOHPoTFvABPkm+sLVwCvGGPqjuQkxn7aehu4DGy/NvaXzfzA1zLGfOr8LH8FnCUiSdggXmKM\necMYU2uM+Rj77+Hco3hfqoU0kDuQMeaPxpjjjTEXY4PjI+zfwfXAdGA1cFcjT03B/ofaGHBsI9C3\nkcceqT7AJid8WnRuEbnW6drYKyJ7gaFOjS1Ra4xJDrg96Zyzn4j8S0S2iUgJ8Ewj59wc8PVAYGhg\nuAO3YvvowYbZeGCtiCwSkdOaqWmnMaYq4PuN2J8L2E8mF4pINDbgZhlj9jRyjvp+297NvvtmGGNK\nsZ+CLnNe7yLsL4TWeBHnF4nzZ8NgP/CzNMZsw35K6I39uZ7e4Od6FkfxvlTLaSC7QER6Aj8EfoP9\nyLnSGFMNfAoc18hTCrEtvoEBxwZgW6ZHa5tzrkCB5z5oOUARORb4E/aXSDdjTDLwFfbj/dH4A1CM\nHSmShO36aHjOwFo2A180CPdEY8xFAMaYL52vewB/Bv7TzMXAHk4A1huA/blgjFkL5GFD6QqaCEhj\nTCGwAtvn3lKNLbVYH6RnAZuNMauO4HyB5gCpIjIO+C6H1t2//gsR6Y3tAirA/lxnNvi5JhhjGmso\nqDamgeyORwG/MaYMWA+c4FzAmort6zuIMaYW+zH5ARFJFJGBwB3AP9qglo8Aj4jcLiKRTkvydOzH\nZ7D9iYMDHp8A1AG7nOfdgG0hH61EbF90iYgMwo5OaE4OECMiN4tIjFP78SIyGkBErnS6K2qxQV9H\n4wEIEAPcLSJRzvufBvwn4P6XgCzsp4Z3mqnpJ8BNInKLiHQVa7yINNXKbfizBXvBt7vzei8181rN\nct73K9j+4Q1Ol1mgC0VknIjEYvvPZxljSrB/75NE5DznZxotIt8SkSGtrUW1nAZyBxORaUCyMea/\nAE7f5jvYlsk04KEmnnoLsB8b2AuBV4HnjrYeY0wF9mLThdiP3Y8CFxtj1jkP+Qv2F8ZeEXnNGLMU\n253wGbZFdYzz9dG6G/v+S4B/8c0vhKbqrsIO45sKbAJ2Ak9hf2EAnAOsEZFSbLhd7IRUY77C/l/Y\ngX2/VxpjAruHXgeGAa87n2SaqmkucKbz2huxn2yeALKbeMr9wMPOaIYfOeeow/6iTQdmNPVaLfQi\nMIrGW/UvA49hf7EOAK5zXr8QOAO4Efvz2Abci21Bq3YmB3cdKqUaEhEPtgvnPGPMog54vRuBs40x\nZxzlebphA3WQMWZ7wPE3sUMwHzm6SlVb0xayUod3BbCrg8I4Adt//pejPI8AtwHvBoaxCm76MUSp\nZojIZ9i+40s64LXOx3YlvI0dK3w09mC7I9p0lqBqX9ploZRSQUK7LJRSKkhoICulVJDQQFZKqSCh\ngayUUkFCA1kppYKEBrJSSgUJDWSllAoSGshKKRUkNJCVUipIaCArpVSQ0EBWSqkgoYGslFJBQgNZ\nKaWChAayUkoFCQ1kpZQKEhrISikVJDSQlVIqSGggK6VUkNA99VRQKc7KEiAJ6NqKWyxQ69xqAv6s\naeRYY4+p5pu96AqdPw+5ef3+uvb7CajOTPfUUx2uOCurD3Csc/M5fw4FegBeIMK96g6rBtgObGlw\n2+r8+ZXX79ddnlWraCCrdlGcleWlQegaY44Fhjlb3YezXcAqYGXA7Uuv31/halUq6Gkgq6NSnJXV\nBRgPTADSndA9VkR6uFtZ0KkF1vJNQK8CVnr9/g1uFqWCiwayOiLFWVmDgYnGmJNqjfl2hMgIEdFr\nEa1XDHzBN0H9CTao9T9mJ6SBrJrkXGA7DphaW1d3CjApwuPp7nJZncFOYC4wB5jj9fu3uFyP6iAa\nyOoAJ4BHGmOmVtfVnR4hMjnC40l2uy5FHvABNqDne/3+UpfrOYiIDAKyjTEjA47dC+wzxjzS4LEv\nOI/9VweWGDL0o2YnV5yVFQOcXlVTc1mEx/N/ER5PVxEhOiKYBzp0OmnO7WagpjgrazFO6xlY4vX7\na9wsrqW0a+vwtIXcCRVnZcVU1NScWVlTc3V8dPRpkR5PF7drUq1WAizAhvM7Xr9/fUcX0FwLGcgE\nPgYmATOBUUAFMALoCdxhjMl2zvEyEO+c4mZjzMciMhW4FzsufCTwOfA9E6bBpYHcSTghfFZVTc3V\ncVFRp0ZGRGgIh6f/AS8Br3v9/uKOeMEWBHKuMeZG5/gLQC/gTGAIMB87Bt0D1BljKkRkGDDDGDPe\nCeS3sAG+Dfv+7jTGLOyI99bR9CNEGCvOyoqtrKk5q7Km5uq46OhTYyMjY2Mj9a88zE1ybo8XZ2XN\nBF4E3vP6/bXt+JpNterqj7/e4Pg/jTF1wFoR+RrbHbMeeFJERmOHCB4b8PglxpgtACKyHBgEaCCr\n4OeEcKYTwtNjIiNjYzSEO6NY4LvObUdxVtarwItev39FO7zWbuzU9UDdsCELsL/BfQ0D3AA/BnYA\nx2Nby4GTaCoDvq4ljHMrbN9YZ7P2zjuHR3g8d3tjY8/XEFYN9MQG3o+Ls7JWYrs0XmmrKd7GmH0i\nUiAi040xc0WkG3AG8Djw/UaecpGIvAgcAwwG8rFT5rcYY+pE5CqCe/p8u9H/tSEsw+eTX51yyndT\n4+N/3iMhYbRHRNyuSQW944BHgN8VZ2W9jw3nN9tgWveVwFMi8gfn+yxjzLom/knmAznYXxQ3OP3G\nTwP/FpGLsP3KDVvVnYJe1AtB7117bWxybOxPeiQk3NQtLq632/WokLcXeAZ4XBdGcpcGcgiZc911\n/bvHxd3bOzHx4rjo6PjDP0OpI1KJbTE/4vX717hdTGekgRwCFlx//eTu8fH+PklJ0yI9nk7Zt6Y6\nVB3wJvA7r9+/xO1iOhMN5CD19wsvlLTU1KtT4uPv7JWYONztelSntQC4z+v3z3O7kM5AAznIZPh8\nUbdNmnR9WmrqPV3j4nq6XY9SjoXAb7x+/xy3CwlnGshBIsPni84cPvx7Jx9zzK8HJCcPdLsepZow\nF7jT6/cvc7uQcKSB7LIMn8/zrYEDTzllyJA/pPfsOUqHrqkQYIBXgF95/f5NbhcTTjSQXXT75Mnp\nGT7f42P79p0aHRGhY8JVqKkEngAe9Pr9e90uJhxoILvg4uOO6/Hd4457+KQBAy5KiImJc7sepY5S\nEXA38KzuyH10NJA7UIbPF585fPgtpw8b9tMeCQm684YKN4uBH7bTehmdggZyB8jw+SJ7Jyaeetno\n0Q+N69fvOO0nVmGsBruGhd/r93fK6c9HQwO5nWX4fP3POPbY+88bOfJ8b2xsgtv1KNVBNgE3ef3+\nbLcLCSUayO0kw+eLPqZr1wsvHT36N8f17j3E7XqUcskr2GDukMXyQ50GcjvI8PmGZvh8D1w4atR3\n4qOjdWcO1dltAq70+v05bhcS7DSQ21CGzxebFBPz3esmTLhrQv/+Ot1ZqW/UYZf9vMfr91e5XUyw\n0kBuIxk+34ARPXv+6oaTTrooNT6+4e4JSilrGXC51+9f7XYhwUgD+Shl+HweYNp5I0b8+vyRIydG\nRUREuV2TUkGuDLjO6/fPcLuQYKOBfBQyfL7EmMjIa26dNOmmcX37DnO7HqVCzKPAz9p5A9aQooHc\nShk+3+Ae8fF3/mzq1HP7eb293K5HqRA1F7jE6/cXul1IMNBAPkIZPp8AJ6b36PGz2ydPnp4UG5vk\ndk1KhbiNwHm6gpwG8hHJ8PkigHOnDx1601Xjxk2KjoiIdrsmpcJEOXCp1+9/y+1C3KSB3EIZPl8c\ncO0VY8dekeHzjdfpz0q1uVrgBq/f/ze3C3GLBnILZPh8qcBtN5500lknDx482u16lApz93j9/vvd\nLsINGsiHkeHz9RW4846TTz7lhH79Rrldj1KdxJPAbZ1tOU8N5GZk+HyDIkR+dte0aVNH9eqlM++U\n6livYyeRdJphcRrITcjw+Y6N8nju/PWpp04ZlpKiY4yVcserwBWdpaWsgdyIDJ9vpEfkx/eedtrk\nY1NSjnW7HhX69paXc+vMmazeuRMR4clzzuH9tWt5Ny8Pjwip8fE8fe659E46dBTlq8uX88iHHwLw\n05NP5rLRo6msqeGyGTPYVlLCtSecwHUTJgBw28yZXHPCCRzfu3eHvr929hx2Zl/Yh5Xu49ZAhs83\nCrjjrqlTx2gYq7Zy1+zZnDp0KC9dfDFVNTWUVVeTlprK3aecAsAzixbxcE4Of/zOdw563p6yMn63\nYAELrr8eEWHKs89yps/Hxxs3MrpPH964/HJOfvZZrpswgVXbt1NnTLiFMcA1QAVwk9uFtDeP2wUE\nkwyf71jg9tsmTUo7rnfv492uR4WHkooKPt64kSvGjgUgOjKS5C5dSIqNPfCYsupqGhtJOXfdOqYN\nGULXuDiSu3Rh2pAhfPDVV0RFRFBeXU1N3Tef5B+YN49fTpvW/m/IHTcWZ2X9we0i2psGsiPD5xsI\n3HHtCScMmThw4Elu16PCx4Y9e0iJi+PGN9/k2888wy1vvcX+KrsC5X1z5zLi0Ud5Y+XKRsO0oKSE\nvgHdGH2SkigoKWHa4MHs3LeP6X/7G7dNmsS7eXmM7tOn0S6PMHJHcVbWz9wuoj1pIAMZPl8v4Kfn\njxw56NShQ6e4XY8KL7V1dawoKODaE07goxtuIC46mj8uXAjAPdOn8+Udd3DRccfxlyVLDnluo52m\nIkRGRPC3Cy/koxtu4NwRI/jzokXcPHEiv5w9mytff5138/La902557fFWVnnuF1Ee+n0gZzh83UH\n7hzXt2+P80eOnK4T8FRb65OURJ+kJMb36wfAOenprCwoOOgxF44axdu5uY0+d2tJyYHvt5WU0Dsx\n8aDH/O3TT7l09Gg+3bKF6IgInr/oogMXAcOQB3ilOCsrLCdodepAzvD5YoFbeyQkdL9x4sQzIj0e\nvcip2lzPxET6eb2sLbQLmuV8/TW+1FTW7d594DGz8vMZlpJyyHOnDxnCvHXr2Ftezt7ycuatW8f0\nId9s0bi3vJz31qzh0uOPp6y6Go8IAlTU1LT7+3JRPDCzOCsr7FZZ7LTD3pxV266L8ngm/f6ss6b2\nSkwc6HZNKnytLCjg1pkzqaqtZVDXrjx97rncMnMmXxUWIiL0T07mj5mZ9ElKYtnWrTz32Wf86Rz7\nyfzlpUt59KOPAPjJySfzvTFjDpz3F7Nnc1ZaGpMHDaKiuppLZ8ygoLSU748fzw9PPNGV99qBFgNT\nvX5/hduFtJXOHMinAlf+cto033G9e09wux6lVKs87fX7w2Y4XKfsssjw+dKA710wcmSihrFSIe3G\n4qys890uoq10ukDO8PlSgFv6eb0VZ6en/5/b9Siljtrfi7Oy+rtdRFvoVIHsLDB/DRBx26RJ02Mi\nI7u4XZNS6qglAy8UZ2WF/BCpThXIwBRgxFXjxvXtn5w81O1ilFJt5hTgdreLOFqdJpAzfL4+wOXD\nUlLKTh069HS361FKtbn7Qr3rolMEcobPFwlcB1TccOKJp0fpXnhKhaN44DG3izganSKQgdOBwd8Z\nPrxrX693sNvFKKXazfnFWVkhe7E+7APZGVVxfkxERMF3hg8P2b8opVSLPVmclRXjdhGtEfaBDFwA\n1H1//PixSbGx3dwuRinV7oYCd7pdRGuEdSBn+HzDgIm9ExOLvzVokK7iplTncWdxVlZXt4s4UmEb\nyM6Y48uB0qvGjZscHRERkh9hlFKtkkQIDoML20AGTgCO6REfXzaiZ89xbhejlOpwtxVnZSW7XcSR\nCMtAdoa5XQjsunT06AlRERFRbteklOpwXkKslRyWgQyMAlISoqMrx/btG/ZrECqlmnR7cVaW1+0i\nWirsAtlZ5/hcYO8lo0eP1fUqlOrUvMCVbhfRUmEXyEAaMFBg70n9++tmpUqpH7hdQEuFVSA7reOz\ngX2nDht2TEJMTEh16Cul2sWo4qyskOi6DKtABnpjW8i7vz1oUFhugqiUapWQaCWH1RZOGT7fuUAm\nsCU6IsJzbEpK18Hdu6f0S0pKSU1I6N49Li7FGxubov3KSnU6+4HeXr+/1O1CmhNuuyyPAaKBAVW1\ntZVf7NhR9sWOHV8B+YEP6pmQ0MWXmpoyMDk5pVdSUkpKXFz35C5dUhJjYrp6RMLtU4NSyq4ElwnM\ncLuQ5oRbID8B9AFSgYHAAOf7SMBgu2jqduzbV7Zj375dwObAJ2urWqmwFvSBHFZdFo1xLvR5ge5A\nCtAXG9b9gK5AHSDOrRIoc261gefRVrVSIa8I6OH1+2sP+0iXhHwgP7SsWu4aE9WqN5Hh88Vgg7o7\nh2lV801QVwSeQ1vVSoWUb3v9/oVuF9GUcAjk64GHsP3Eec6f9V9/ddeYqOojPWcTreoBQH+0Va1U\nKHvI6/f/wu0imhKSgZw+JXMQdjbelosfeOkXMfGJY5t4aA2wnoNDOh/Iv2tM1M7WvLa2qpUKaZ97\n/f7xbhfRlFAN5BuAiYmpvSPO/cWTl4nH05rtv/fQvq3qPtiw1la1UsGjCkj0+v1VbhfSmJAbZZE+\nJbMLMA7YNOzEU0e0MozBhuRJzi1QzUPLqo+4VT0rP98Ae53busD7Mny+aL4J6lRsi3ogOgJEqY4W\nDYwElrpdSGNCLpCBY4EIoLbHkPQh7XD+SGCYc8sMvOOhZdWtalXPys+vAgqc2wGHaVX3IKBV3eJx\n1YmJ3VPi41O0Va1Uk8ahgdxmRmL7hknuPaCjd5AO+VZ1t7i4lGRtVavOralrTq4LqT7k9CmZAjwC\n1PQdPjZh+g/vudHtmlqgqVb1urvGRB1xP5bTqk7CBnXb9FVrq1p1Lou9fn9QrgQZai3kVGzobOo/\n6sTj3C6mhZpqVdc6rer6oD6SVnWxc9NWtVJHbqDbBTQl1FrIJwHXA5vOuPXBc3sMHn682zW1k/pW\ndWBQt2WrujcwCG1Vq86pDogOxhl7odZCHokzpje+a2oPl2tpT8Heqt7iHAe0Va1CjgfoCWxzu5CG\nQi2QhwD7xOORLknJqW4X44IIYKhza2oEyBG1qg8zAqSpVrWOAFGhrg8ayK2XPiUzGhsEW3oOGdHN\nExEZMrV3EG1VK9VyfdwuoDGhFGqp2P/QJnWQrzO2jltLW9VKHSrR7QIaE0qB3ANny6n4rqkhs613\nkGtpq/pAYLdRqzoF26LWVrVyS1D+Yg+lQO6F858zJj4xzuVawt2RtqrzsbMVtVWtQkVQ/psIpUDu\nDlQDxMQlxLtcS2cWUq3q4T16dPv5lCnXxkZF6S9xFai1a+C0q1AK5K7YlZqI7hKvgRx83GpVd8cG\n9CC+aVUD7AOKVu/cWfSXJUtevXHixKsiPZ6oo3yPKnxoC/koJeO0kKNi47S1E1o6ulU9EPgJ9sJN\n6ccbN27t1qXLG5eNGXOpRyQoW0aqwwXdpBAIrUBOwglkT0REKNWtmtZereq1GT7fo8DPsQtRlWfn\n5a3tHheXnZGW9p12eScq1BS5XUBjQinYkoCdACaU5nur1mpxq7oLhWvLSckNbFXPys9fk+Hz/Rm4\nBduvXP3i0qVLu8bFJZ00YMCUDnoPKnjtdruAxgRlP0oTBOdijQZyp1bfqs7Edkv8JVG2zE+PmLHj\noWXVBy04NSs//zPgH9i+5QiAxxYuXLB6585lHVyzCj6t2sKtvYVSIBvqr4xqIKsAReZYzoy6nm9H\n3ntRI3d/AGRjZxMKwIPz5mVv3rt3bUfWqILOVrcLaEyoBXL9lxrI6oAa4thvenFi5B/uJE8OWgHQ\nuQD4b+B/2FCmuq6u7jdz575RuH9/0K1loDpEkdfvL3e7iMaEUiDXTxCgprqq0uVaVJApNGlESmUM\n8C55MiDwvln5+bXAC8BqoB9AaWVl9YPz579aWlm5p8OLVW7LdbuApoRkIFeV7dvnci0qyOw2afVf\n9gFmkyddA+93Rl88DWzHLr3ItpKS/Y9+9NE/KqqryzqyVuW6FW4X0JRQCuT9OKNCKkqLS12uRQWZ\n3XVpgd8OB2aSJ7GBB2fl5+8D/ohdU7s7QP3EkZq6uiY3qVVhZ7nbBTQllAJ5N3YLb8pL92ogq4ME\ntJDrTQb+Qd7B61jMys/fDfwBiMJZ8evjjRu3vrZ8+Rt1erG4s9AWchvYDcQAlO3drYGsDlJYd0gg\nA1wAPNbw4Kz8/C3Ao9jZn10AsvPy1s7Oz89uzxpVUKgFVrldRFNCKZB34rSQ927fvNflWlSQqaA7\n+02jy2TfQp78rOHBWfn5a4A/Y1cRjAJ4aenSpYs2bcpp10KV25Z7/f4Kt4toSigF8h6cegvWrNhV\nV1sblHPRlXt2N95KBniIPLms4UGdONIpzXK7gOaEUiAXYUdaUFtdVVdesicoZ9oo9zTSj1xPgOfJ\nk+mN3KcTRzoXDeQ2UkDAGqalu7cXNPNY1Qk100IG2931H5040qntARa7XURzQimQ92KHK0UBFG/f\nvN3dclSwKWy6hVwvCZilE0c6rTlevz+ouzpDJpBzc7IN8BXOUKXta7/Y4m5FKtg002URqDc6caSz\netvtAg4nZALZsQaIB9i48pOC6sry/S7Xo4JIqelPpUloyUN14kjnUwL8x+0iDifUAnkD36z4xp5t\nG9c1+2jV6RQZX0sfqhNHOpfXvX5/0H/SCbVAXocdaeEB2L52lV4JVwc5zIW9hi4AHm94MGDiSFd0\n4ki4eM7tAloipAI5Nye7ArtTRDLAV4s+WGfq6rTVog5owYW9hm5uZuLI0+jEkXCQ6/X7F7ldREuE\nVCA7lgAJAPuKdpbvK9qx2eV6VBA5whZyvYfIk8sbHtSJI2Hjb24X0FKhGMhrAr/Zkrt0pVuFqODT\nwpEWDenEkfBVBPzV7SJaKhQDeQdQiDPaInfem1/qNGpVb48ZQq2Jas1To9CJI+HoMa/fHzLrp4dc\nIDvjkT8AugHs31tYUbTl69XuVqWChSGSIjO0tU8/ookjD8yb94pOHAlqxcATbhdxJEIukB1LsR8f\nBeCrJXOXuluOCiat7Lao1+KJIwWlpWU6cSSoPen1+4vdLuJIhGQg5+ZkF2JbK90B1nz8/vqK0uLd\n7lalgkUrL+wFOqKJI88uXvxKdW2tThwJLvV/VyElJAPZMQenHxljWPfZgoXulqOCxVG2kOtNBl5p\nycSRTzZt2vb6ihU6cSS43Of1+0OukRbKgfwldjpkHMCyd15ZWVm2L6Q+nqj20QYt5HrnoxNHQo4x\nJp8QbB1DCAdybk52NfAmkApQV1Ndt/7zD7WVrNhtfBgjh39gy+jEkRAjIrd6/f6Q7EIK2UB2fAKU\nA7EAy7L/sayqoixkhrio9lFDHMVmYFueUieOhI43vX7/+24X0VohHcjOVOq3gB4A1ZXltRuWLtRW\nsmqrfuR69RNHTm3kPp04EiSMMeXAHW7XcTRCOpAdC4EqnB2pP/3v3z8tL91b6G5Jym1t2I9cLwr4\nt04cCV4i8hOv37/e7TqORsgHcm5O9n5gJrYvj9rqqrqV778R1PtmHYnqygqeuuJbPH7xOP544fHM\n+XMWAEVb1/PUlZN45Jx0Xv35ZdRUVx3y3M1ffMoTl4zniUvG8/jF4/hy3psA7Nuzi2eumcpjF43m\ny/lvHXjN2OlqAAAaLElEQVT8Sz8+n5Jd4ZEhrVhkqCXqJ44c1B+iE0fcZ4x5x+v3/9ntOo5WyAey\nYx52i6dEgPyP3v26aOv6fHdLahuR0TFc9+z73Pb659w64zPWfPI+m1YuZvYTv2Ty5bfy07dy6ZLU\nlc/efP6Q5/YcMoKb/rGIW1/7jO8/mc1/H7iJ2poaVsx+nbGZV/CjFz7io5ceBWB1TjZ90saQlNqn\no99iu2jjLotAvbGh3NjEkaewez/qxJEOVGdMoYhc43YdbSEsAtnpS34JZ7A+wJJ//fW9cFjjQkSI\nibO7YNTWVFNXUw0irPt0ASOnXwDA2MwryJ0/85DnRneJIyIyEoCaqgpE7MiDiMgoqivLqamqRMRD\nbU0N/3v1T5x85U866F21v3bosgjU1MSR/cBj6MSRDuURucbr94fFLvRhEciO5dixyT0Adq5fvWfT\nik8+crektlFXW8sTl4zngVP7MvTE6XTvN5jYhOQDYevt2ZeSXVsbfe6mVUv444XH8/h3x3LuL58k\nIjKS0WdcwtpP5vD8zZlM/+E9LHrjGcZkXk50l7iOfFvtqoJu7Dep7fkSh5s4Eo1OHGl3xpg/e/3+\noN8rr6XCJpCdRYdmYAfqRwAsfPWJj/btCf1OUU9EBLe+9hl3zV7Pli8/Y+f6vEMfJI2Pux0wagI/\n/tcKbnr5YxY8/zDVlRXEJnq5+om3uPmVRfQdPoa8j95l5PTz+c99N/DKnRezcUVIrOV9WO3cSobm\nJ478AZ040q5q6uo+FpHb3K6jLYVNIAPk5mRvAd7BubBSV1Nd9/GMJ/9TV1tT425lbaNLYjLHjDuZ\nzasWU7FvL/Vvq3jHVpJSmu/77TF4ONFd4tmx7suDjs/9ywNMu/YuVsx+nb7Dx3KB/6+8/9Q97fYe\nOlI79iMHupk8+XnDgzpxpH1V19Zui/R4zg3VCSBNCatAdrwNbANSALavWbl77aIP5rhbUuvt27OL\n8tK9AFRXlLNu8TxSj0lj8PgpfDH33wAszX6Z4VO/c8hzi7auPxDae7ZtZNeGNXTt/c0AgcJNaynZ\ntY3B406muqIMEQ8iQnVlRQe8s/bXAS3ker8lT77X8GBTE0dyd+zQ1QmPQm1dXUVURMSZXr9/l9u1\ntDUJx26t9CmZA4AsbDBXI8LZP3/8e8m9+g9xubQjVrBmJW/4r8XU1mJMHaNOu5Dp199N0ZavmfGL\n71FWvIc+acdz8f0vEhkdQ27O22zN/ZzTfnQvS7P/Qc4LvyciMgrxeDjlB79ixLRzDpz71Z9fyuk3\n/YaUAcPYV7STl++4kIp9xZz2Iz8jp5/v4rtuG4M8c7gk5qyOerlq4EzSzAeBBzN8PgEuAs7C7ppu\nojwezwNnnHHJgOTkYR1VXLgwxpg6Yy7qlpX1b7draQ9hGcgA6VMyzwAuBdYDeHv2i8+4/aHro7vE\nJ7lbmeooibKZm2I79HdwCXAyaWZF4MEMny8CuBaYCGwESIyJifrtGWdcnRIfHx7jDDtIVU3Nr1Pv\nu+8+t+toL+HYZVFvDnaH6p4AxTu27F/0z2deD5f+ZHV4paY/lSahI19SJ460o7KqqqfCOYwhjAM5\nNye7Fru5YS32Pwobli3clrvgbb3S3YkUGV9Hv2T9jiPdAg82NXHkDx9++HJFdfX+ji4y1JRWVr7R\n+4EHbna7jvYWtoEMB3YWeQK7/140wNK3X1qxNW/ZYlcLUx2mAy/sBUqjhRNH8nbt2vPs4sWv6sSR\nppVUVGQnxsRc4nYdHSGsAxkgNyd7DfAi9qOiB2D+3377fvGOLV+7WpjqEO20pkVLTOIIJo68ZieO\n1HV8mcGtuKJiblJs7Llev79T/GzCPpAdC4C52OFH1NVU173/5D2v7w+DSSOqeS61kOu1eOLIO3l5\na2fpxJGDFO7fP8sbG3uG1+8P+SUQWqpTBHLALL61QF+A8tK9Ve8/5X9Fl+oMbx00OaQ5LZk4Eg3w\n8tKly3TiiLW1uPifKfHxZ3n9/k51Eb5TBDJAbk52FfAnYCfOUp2lhQVlc5+972Xdiy987TFDqDVR\nTd6/twQuvA3SzoThZ8EnDfb6+P3fYfR59jbyOxAxAor2wq4imHy5PfZmwMjjc26CbYcuc3O4iSP9\n0IkjB3xdVPRs+qOPXuz1+8NzTG4zOk0gA+TmZJdiPyruw5nJV7Tl65Kc5x9+ubqyQpdIDEOGSIrM\n0Cbvv+1BOGMy5L0LK/4LwxsMW77zWlj+X3v77R0w5QTolgwz3oGrzoFPXoPfP2cf+/Z8GJsOfXoc\n8jICPNfSHUd+O3/+O5s64Y4jdcaYrwoLfzPm8cdvcLsWt3SqQAbIzckuAn4P1GFHX7B97ardH774\nyIvVFeW6H18YaqrbomQffPgZXHuh/T46GpKbmTY04x249Ez7dVQklFdCZRV4PFBTA4+9BHc2vSpv\nFPAf8mR04MEmdxz54IM3du3f3/gSfmGoqra2Om/nzpvH/elPfrdrcVOnC2SA3JzsHcAj2L47L8DW\n3M93zvvbg89r90X4aerC3tebIbUbfP+XMOZ8uO5u2N/E56Sycpi9EC443X5/WSa8txDO+AHcexM8\nPQOuPAfiujRbSiLwbksmjuyrqqp+cN68V0sqKoqO4K2GpOKKipLFmzadOfHpp592uxa3dcpABsjN\nyd4EPIzdsbobwI6vvij64Jms5yv2FYf9f4LOpKkWck0tLM2FH10Cy/4D8XHw0F8bP8fb82HSGNtd\nAeBNhHeehc/+ZbspshfABafBD+6xfdIN+6IDHNHEEWfHkbCdOLKluHjD26tXT8h84YUPDv/o8Ndp\nAxkgNyf7a+BBbN9dCsDuTV8Vv/enu58rKy4Kix0IVNMt5H497e1EZ9vSC0+3Ad2Y196FS5tYp+g3\nT8Ovfmi7NMaNgOcegF8+1mxJOnEE+GL79gXPLFp03E1vvhkW2621hU4dyAC5OdmbsaFcRcC6F7Mf\n/8ULJbsKNrpanGoTu40PYw5dwL9XKvTvDfnOPsVzF0F6I9f/iksh5zM455RD71u7wY6qmDIByips\nf7IIVFQetqyWTBxJgvCbOFJVW1vz0fr1j90/b96pf/r441K36wkmYbva25FKn5KZAtwJJGM/NhIZ\nHRsx/Yf3nNVzSPoYV4tTR+2GmGNJ9mw45Pjy1XDdPVBVDYP7w/MPwOvOnuU3OJN1X/gvzP4IXnv0\n0PN+98fwwG0wbBDs3A3n3mwD/De3ftPffBhPkWYOWaMhw+c7FrgL2AWUA1wxduyYs9LSzm7RWYPU\n9tLSXXPWrv3BzW+99dbhH935aCAHSJ+S2RW4FRgIbAYMwLcuvXnikAnTThPxNL5Pkgp6F0WfzZCI\n2W6X0ZS7SDO/a3gww+cbD9wCbMV+guO2SZOmTBw4cGrHlnf06owxSzZvXvz6ihWXPffZZ+vdridY\ndfoui0C5Odl7gN8BnwLHAJEAH8948pPPZ740o7a6usrN+lTruTyF+nBaPHHk8f/9LyfUJo6UVlaW\nzVi+/OHHFi6crmHcPA3kBnJzsiuAZ7FjQwfgrDWQO/+ttQue/93fdQRGaHJxkaGWOKKJIw/Mn58d\nKhNHcnfsWPvYwoWZb69e/YtZ+fk6+eowtMuiGelTMk8AbgBKgb0AXRKTo6f94JdnpwwYNsLV4tQR\n6ev5mCtiprpdxuGUYnccWR54sLEdRxKio6N+m5FxVWp8fN+OL/Pwiisq9s3Mzf3nO3l5P5+Vn6/r\nxbSQBvJhpE/JHIztx0vA9uUBcML5143zTfq/MzwRkZGuFadaLJYibu/Sy+0yWqIAmEiaOWiET4bP\nFw3cDhwLbAHonZgYl3XaadcmxcZ2O/Q07qirq6v7ZNOmL2esWOEv3L9/pjPpRbVQuwWyiPwKuAy7\nY0cd8ENjTKMLw4vIvcA+Y8wjR/F6C4CfGmM+a+05mpI+JdMLXAOMwV7sqwbofezxKd+67JYL4pO7\nh8T/9M7ulth+xEtIDC/PAyaRZg7qHsvw+eKxIy9SgB0AaampXe+aOvXa2Kio+I4v82AFpaWFM5Yv\nf2XJ5s0Pz8rP16VtW6Fd+pBFZCKQCYw1xhwHnIoNsnYhIhHtdW6A3JzsYuzOI68BfXBm9hWsWVH4\n1oM3/23zF59+rJ80gl+QX9gLFFITR8qqqspn5uZ++LN33jlvyebNd2gYt157XdTrDRQaYyoBjDGF\nxphtIrJBRFIARGS806qtd7yIzBORtSLyA+cxU0XkwKLdIvKkiFztfL1BRH4tIgux26wDfE9EPhaR\nL0RkgvO4Cc6xZc6fPuf41SLyHxGZ7bzmw829odyc7NrcnOx3gd9g/0MMADw1VRW18//24JzF/3r2\npary/TrIPYgF+YW9hiYBrzYzcSQKlyeO1NTV1X64fv2qO9999+evLl9+zszVqxfOys8Pi8krbmmv\nQH4f6C8ia0TkaRGZ0oLnHAechb1w8WsRacn26BXGmMnGmNec7+ONMd8CbgScRRHJA042xowBfo2d\nlVdvNHAxMAq4WET6H+4Fc3Oy1wN+IAc7XjkeYM3/3luf/fs7/rx97arPjanT5nIQCqEWcr3zsJ/M\nDuLsOPIodhJTh+84Yoxh1fbtX9/93nvPPP3JJ5fuLit7clZ+/t6OeO1w1y6BbIzZB4wDrsfONHq9\nvmXbjLeMMeXGmEJgPjChBS/1eoPvZziv/yGQJCLJ2NXc3hCRL4A/AoGjI+YaY4qNMRVALjZgDys3\nJ7sceAn78TEe240h+4p2lr//1K+zFzz38F9KCws2teRcquMEwe4hrXETeXJXw4MBO470JmDHkU82\nblzQnsVs2ru34JEPP/znA/PmXb1hz57bZ+Xnf+ksIaraQLuNEDDG1GL3slsgIquAq4AavvklENvw\nKY18H/j4xp7TcBWsxs5xHzDfGHOeiAxyaqoXuOJALUfw83C2hVqWPiXzbuBS7C+QvcCezasWb9+8\navHzx2dcMmL4yZmnR3eJb2aVXdVRdhuf2yW01oPkyRbSzD8CD87Kz/8sw+d7GbgCOxyu9vH//S/H\nGxublN6z59i2LODroqLNb3355YrFmzf/HXhfxxS3j/a6qOcTkWEBh0Zj/8FswLacAS5o8LRzRCRW\nRLoDU7Gz5TYC6SISIyJeYPphXvpi5/UnA8XGmGJsC7l+uNrVrXpDzXAWvH8a+C12J5JBOL84Vsx6\n7cv/3vejJzcs/zinrramU+0NFoxKTX8qTYLbZbSGKxNHjDHk79q1/rfz58/85ezZWYs3b/7+rPz8\nNzWM20+7DHsTkXHY/euSsa3cr7DdF8OBv2OH7CwGxhtjpjrD3voAQ7D/sB42xvzVOdfDwDnYDUqr\ngJnGmBdEZIPz/ELncQuAT4Ap2Isd1xhjljgjPl7Edp3MA64wxgxyulDGG2MXdnEuHj5ijFnQ2ved\nPiUzEpiM/cUQDWzDtrxJGTjMe+KFPzy9e/8h6a09vzp6V8VMpLfnc7fLaK0OmThSZ0xd7o4dX7+x\natXK/F273gFm68iJjqETQ9pB+pTMJOywv9OwK3UdGPw6bOLpg44/4+KMOG+3Q3deU+0uM+r7jIx8\nxe0yjka7TRypraurXVFQsPafK1eu2LBnz9vAnFn5+SExcDtcaCC3o/Qpmf2xk2PSgUJsCwdPRKSc\ncN4144dMmDYtMjq2+U1/VJs6KfJ3TI26x+0yjlabThypqK4uW7pt27p/rVq1cltJyZvAvFn5+bpm\niws0kNtZ+pRMwfahXwF0xbZwqgDiu6bGjv3OFRP6jRg/ISqmi+szrTqDYZ63uCDmosM/MPj9DziV\nNFMReDDD5+sO3I29QL0bYOKAAX1unDjx6qiIiKj6xxlj2FpSsmH+unXr56xd+1VVbe3bQM6s/PyS\nDnwPqgEN5A6SPiUzFntR8lzsxZft2P51omLjIkefeenxx4z99sTYBG93F8sMe90kn+tjR7ldRlv5\nL3AhaQdPCMnw+foC9wBlQAnAWWlpwy4fM+aSiurq/Uu3bVuTvXr1+g179hQA7wALnVmAymUayB3M\n2ZnkdGAado3bndiZfyDCyFPO8w2beNqkxJReh52koo6cUMNPY71ESNhsUdfSHUfifKmpg78qLCyt\nNWY59gL36ln5+Tr6J4hoILvEufA3GTs7MQ778XJf/f2Dx0/pN3zq2d/q1ndQmu5U0raujTmeVM9q\nt8toS78gzTzU8KCz48it2JE+e7AzaJdo/3Dw0kB2mdOVMQ7blZGCvfB34D9MzyEjuh33f9+d2HNI\n+mhd6rNtnBt9MWkR/3W7jLZkgCsbThwByPD5RmG7xtboUpjBTwM5SKRPyYwARgJnY8djV2CvlBuA\npNQ+caPPumxC3+HjToiKiY1zr9LQ9+1IP5Oifut2GW2tGjiTNPOB24Wo1tNADjLOqIzBQAYwFvtx\ncwfOBcDoLvGRw6d8x9d/5ISRyb0HDPNERLTr0qPhKD1iBmdHX+V2Ge2h0YkjKnRoIAex9CmZvbAj\nM+ovAO7BuWoOEJ+cEjt8SubwvunjRial9jlGPNrX3BI9ZRnfjz3R7TLaWj52Q9SXSDO6sFWI0kAO\nAc6OJeOxa3z0w+7AUkTA4krenv3ih0/JHNHHN2ZUQvce/VwpNEREUsZPYrsiEtr/9ssr2L9yDV/N\n+pAdS3O5ZuY8s/Xwz1LBTAM5hDjdGb2wE01OwV4ErMXOAjwwQSB1kC/ZNzljZK9ho0bpFO3G3RBz\nLMmeDW6XccRK97N37UbWLfycXQuWsKOmlu3AXODDmfNM5eGer4KbBnKIcsJ5AHaExhQgEdvPXIgz\nExCg7/CxqUNPOm1Ur6EjRsbEJ3Z1pdggdFH02QyJmO12GYdVW0ttwS42frGW9fOXsHv1OvZjPxkt\nwK6IuHnmPP1PHC40kMOAM0LjGOyazJOxy39WYcP5wMD/PmljUgccf9Lg1IG+IUk9+gyMiIyKdqXg\nIHBK5M+YEPWY22U0al8ZJV9vYe2SlWybv5i9pfupwY5R/9S5fTVzntEJHWFIAznMpE/JjAKGYZdi\nPBG7pkH9xIAD69hGREV7jhl3cv++w8cO7t5/yJD45JQ+nemi4HERz3Fm9A1ulwFAXR11OwrZnLuO\nrxcsoXBFPvuxwx3XAYuwF+y2zZzXsXvmqY6ngRzGnEknQ7GrzY3H9jkLdirtXgK6NrokdYsZNGZS\n/55DRgzs2mfggPiuqX3DeUhdX8/HXBEz1ZXXrqikfHshWzZsZfOKfHYvWUlF6X6qsdcBPgOWYVvB\n+5o/kwo3GsidhNPn3A076eR47IXB+qU/y4FiAgI6KjYucuDob/XtPWzUgK59jxkY3zWlVzitSBdL\nEbd36dXur1NTS03RXnZs28W2dZvY9ukqinLXUYvdrUewC8ovwi6puWXmPKOz6ToxDeROKn1Kpgfo\ni93YdRR2lmAsNigqsS3og5Z2TEzpHddr6MjUbv2O6ZHUo2+P+K6pqXHerj1CdU3nW2L7ES9tt/56\nRSXle0spLNhFwYYtFKzIZ/fKfCpraonlm/0eNwBfYLsjNs6cZ4rbrAAV8jSQFXAgoHtgR26MwAZ0\nV2yQeLBTc+uv8B90Qcnbs198z6EjenTre0xqUmqfHvFdU1O7JHXtERkd03BT2qByWfSpDIj4sMWP\nNwb2l1NSso+iomL2FO6hqGAXezZuoyjva8qKionGLhRV3wLei9167EtgE7YfuKrpV1CdnQayapTT\nxZEIpPJNUA8G+mNb0nUcHNRlNAjq5N4DE3oOSe+R3Kt/95gEb3xMXEJ8TFxCQlRsXHxUbFx8VEyX\nhIgo90Z6nB51M2Mj/3Lg+6pqqiqrKKuopGx/Ofv3FLNnZxFF23ayZ8NWivLXU1ZWQTS2qyca+zOo\n/4VVhN07Mg+7l2LBzHmmtMPflAppGsjqiDhBnYQN6VTsLtuDsIFdvyOFB9sfXen8We38ecg/tqjY\nuEhvz77xCd16xscnpyR0SUqOj01Mjo+JT4yPjktIiO4SHx8RGRUt4vGIiCAiIuJx/hRE7HEOPi4i\nHueY1NXV1dbVVFfWVldV1pRuiasu34fHY3anRm/cF1v1dcXat+/7aPsuysorMUAMNnC7YKer12H7\neutbvAXYPeu2YkN4D1A0c55p1U7MIlILrMKOhlmP3YR3b2vO1ci57wX2GWMeaYvzqfangazahBPU\nXmxQ17eou2O7PbpiW9sebMCBDbn6YXY12MAODO+2vrgVAUSkysoTo9g/yCM1W2OlZE2D+2ux61Jv\ndW4FfBO6e9qju0FE9hljEpyvXwTWGGMeOILnRxjT+IVADeTQo+vrqjaRm5NtsC3IvcCahvc7gR0L\nJADxAbdEvgnubkAytuVdfyEssMVQ/7U0c7zh9/W3KqC82Az6MkaKv4o0FUtipeQjbFdLGbbbpcrl\nWW+fAMcBiMhU4KfGmEzn+yeBz4wxL4jIBuA57M4zT4pIInA9thvlK2wru1UtduUuDWTVIZzALndu\nuw73+PQpmZF801UQGKyeFn5tsF0mlUBlbk52UE+qEJEI7Mp+f2/hUyqMMZOd53Y3xvzV+fp+4Frg\nT+1SqGpXGsgqKOXmZHeWqcFdRGQ5th/+c2BOC5/3esDXI50gTsZ+AnmvTStUHcbjdgFKdXLlxpjR\n2PHg0cBNzvEaDv7/2XAIYeAu0S8ANxtjRgFZjTxWhQgNZKWCgDGmGLsh6U9FJAo7gy9dRGJExIvt\nzmhKIlDgPO/y9q9WtRftslAqSBhjlonICuASY8zLIvJPYCV2csmyZp56D7AYG+KrsAGtQpAOe1NK\nqSChXRZKKRUkNJCVUipIaCArpVSQ0EBWSqkgoYGslFJBQgNZKaWChAayUkoFCQ1kpZQKEhrISikV\nJDSQlVIqSGggK6VUkNBAVkqpIKGBrJRSQUIDWSmlgoQGslJKBQkNZKWUChIayEopFSQ0kJVSKkho\nICulVJDQQFZKqSChgayUUkFCA1kppYKEBrJSSgUJDWSllAoSGshKKRUk/h+YkxglVkpYmgAAAABJ\nRU5ErkJggg==\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x1f2dc4a1240>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "labels = [\"Urban\", \"Suburban\", \"Rural\"]\n",
    "colors = [\"lightcoral\", \"lightskyblue\", \"gold\"]\n",
    "sizes = [per_urban_cities, per_suburban_cities, per_rural_cities] \n",
    "explode = (0.08, -0.01, -0.01)\n",
    "plt.title(\"% of Total Fares by City Type\")\n",
    "plt.pie(sizes, colors=colors, explode=explode, labels=labels,\n",
    "       autopct=\"%1.1f%%\", shadow=True, startangle=300)\n",
    "#plt.axis(\"equal\")\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "2375"
      ]
     },
     "execution_count": 35,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Total Rides By City type\n",
    "#len(ride_sharing)\n",
    "rides_ride_sharing = ride_sharing.ride_id.sum()\n",
    "rides_ride_sharing"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[68.42105263157895]"
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "urban_cities = ride_sharing[(ride_sharing.type == \"Urban\")]\n",
    "#len(urban_cities)\n",
    "rides_urban_cities = urban_cities.ride_id.sum()\n",
    "#rides_urban_cities\n",
    "per_rides_urban_cities = [((rides_urban_cities) / (rides_ride_sharing)) * 100]\n",
    "per_rides_urban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[26.31578947368421]"
      ]
     },
     "execution_count": 37,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "suburban_cities = ride_sharing[(ride_sharing.type == \"Suburban\")]\n",
    "#len(suburban_cities)\n",
    "rides_suburban_cities = suburban_cities.ride_id.sum()\n",
    "#rides_suburban_cities\n",
    "per_rides_suburban_cities = [((rides_suburban_cities) / (rides_ride_sharing)) * 100]\n",
    "per_rides_suburban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 38,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[5.263157894736842]"
      ]
     },
     "execution_count": 38,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rural_cities = ride_sharing[(ride_sharing.type == \"Rural\")]\n",
    "#len(rural_cities)\n",
    "rides_rural_cities = rural_cities.ride_id.sum()\n",
    "#rides_rural_cities\n",
    "per_rides_rural_cities = [((rides_rural_cities) / (rides_ride_sharing)) * 100]\n",
    "per_rides_rural_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x1f2dc3effd0>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "labels = [\"Urban\", \"Suburban\", \"Rural\"]\n",
    "colors = [\"lightcoral\", \"lightskyblue\", \"gold\"]\n",
    "sizes = [per_rides_urban_cities, per_rides_suburban_cities, per_rides_rural_cities]\n",
    "explode = (0.08, -0.01, -0.01)\n",
    "plt.title(\"% of Total Rides by City Type\")\n",
    "plt.pie(sizes, colors=colors, explode=explode, labels=labels,\n",
    "       autopct=\"%1.1f%%\", shadow=True, startangle=240)\n",
    "#plt.axis(\"equal\")\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 40,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "3340"
      ]
     },
     "execution_count": 40,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Total Drivers By City type\n",
    "#len(ride_sharing)\n",
    "driver_ride_sharing = ride_sharing.driver_count.sum()\n",
    "driver_ride_sharing"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 41,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[78.05389221556887]"
      ]
     },
     "execution_count": 41,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "urban_cities = ride_sharing[(ride_sharing.type == \"Urban\")]\n",
    "#len(urban_cities)\n",
    "driver_urban_cities = urban_cities.driver_count.sum()\n",
    "#driver_urban_cities\n",
    "per_driver_urban_cities = [((driver_urban_cities) / (driver_ride_sharing)) * 100]\n",
    "per_driver_urban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 42,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[18.83233532934132]"
      ]
     },
     "execution_count": 42,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "suburban_cities = ride_sharing[(ride_sharing.type == \"Suburban\")]\n",
    "#len(suburban_cities)\n",
    "driver_suburban_cities = suburban_cities.driver_count.sum()\n",
    "#driver_suburban_cities\n",
    "per_driver_suburban_cities = [((driver_suburban_cities) / (driver_ride_sharing)) * 100]\n",
    "per_driver_suburban_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 43,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[3.1137724550898205]"
      ]
     },
     "execution_count": 43,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rural_cities = ride_sharing[(ride_sharing.type == \"Rural\")]\n",
    "#len(rural_cities)\n",
    "driver_rural_cities = rural_cities.driver_count.sum()\n",
    "#driver_rural_cities\n",
    "per_driver_rural_cities = [((driver_rural_cities) / (driver_ride_sharing)) * 100]\n",
    "per_driver_rural_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 44,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x1f2dc890eb8>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "labels = [\"Urban\", \"Suburban\", \"Rural\"]\n",
    "colors = [\"lightcoral\", \"lightskyblue\", \"gold\"]\n",
    "sizes = [per_driver_urban_cities, per_driver_suburban_cities, per_driver_rural_cities]\n",
    "explode = (0.08, -0.01, -0.01)\n",
    "plt.title(\"% of Total Drivers by City Type\")\n",
    "plt.pie(sizes, colors=colors, explode=explode, labels=labels,\n",
    "       autopct=\"%1.1f%%\", shadow=True, startangle=230)\n",
    "#plt.axis(\"equal\")\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.5.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
