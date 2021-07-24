# Ai338-summ2021
LEADER:

a. JAWAD LODHI (61845)

MEMBERS/PARTNERS:

b. SAAD ALI SIDDIQUI (61925)

2. A short description of what we did?

ANSWER:

We have done a Python code (juypter lab) and did Split Training Data for Cross-validation for both 'test' and 'train' files which were given
first we imported libraries on python then started coding by uploading test.csv and train.csv file then we scatter file by using matplotlib library
then initialize values in 'X' and 'Y' then checked its lenght, we also used 'from sklearn.linear_model import LinearRegression' library to cross validate
dataset properly and in the last just check our score.

3. What insights you gained from this assignment?

ANSWER:

If we have huge amount of dataset we can split that data into some ratio i.e 80%, 20% or 70%, 10%, 10%
and can find an accurate result after shuffling these type of cross validation use in different companies or industries
which have some huge amount of datasets.

CODE:
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "engaging-glass",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>PassengerId</th>\n",
       "      <th>Pclass</th>\n",
       "      <th>Sex</th>\n",
       "      <th>Age</th>\n",
       "      <th>SibSp</th>\n",
       "      <th>Parch</th>\n",
       "      <th>Fare</th>\n",
       "      <th>Embarked</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>892</td>\n",
       "      <td>3</td>\n",
       "      <td>0</td>\n",
       "      <td>34.5</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>7.8292</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>893</td>\n",
       "      <td>3</td>\n",
       "      <td>1</td>\n",
       "      <td>47.0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>7.0000</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>894</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "      <td>62.0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>9.6875</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>895</td>\n",
       "      <td>3</td>\n",
       "      <td>0</td>\n",
       "      <td>27.0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>8.6625</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>896</td>\n",
       "      <td>3</td>\n",
       "      <td>1</td>\n",
       "      <td>22.0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>12.2875</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   PassengerId  Pclass  Sex   Age  SibSp  Parch     Fare  Embarked\n",
       "0          892       3    0  34.5      0      0   7.8292         1\n",
       "1          893       3    1  47.0      1      0   7.0000         2\n",
       "2          894       2    0  62.0      0      0   9.6875         1\n",
       "3          895       3    0  27.0      0      0   8.6625         2\n",
       "4          896       3    1  22.0      1      1  12.2875         2"
      ]
     },
     "execution_count": 1,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd\n",
    "df = pd.read_csv(\"test.csv\")\n",
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "catholic-space",
   "metadata": {},
   "outputs": [],
   "source": [
    "import matplotlib.pyplot as plt\n",
    "%matplotlib inline"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "blind-dubai",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.collections.PathCollection at 0x7fb60c0abd90>"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.scatter(df['PassengerId'],df['Embarked'])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "opposite-mediterranean",
   "metadata": {},
   "outputs": [],
   "source": [
    "X = df[['PassengerId']]\n",
    "Y = df['Embarked']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "touched-ideal",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>PassengerId</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>892</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>893</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>894</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>895</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>896</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>413</th>\n",
       "      <td>1305</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>414</th>\n",
       "      <td>1306</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>415</th>\n",
       "      <td>1307</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>416</th>\n",
       "      <td>1308</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>417</th>\n",
       "      <td>1309</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>418 rows × 1 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     PassengerId\n",
       "0            892\n",
       "1            893\n",
       "2            894\n",
       "3            895\n",
       "4            896\n",
       "..           ...\n",
       "413         1305\n",
       "414         1306\n",
       "415         1307\n",
       "416         1308\n",
       "417         1309\n",
       "\n",
       "[418 rows x 1 columns]"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "X"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "intelligent-style",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0      1\n",
       "1      2\n",
       "2      1\n",
       "3      2\n",
       "4      2\n",
       "      ..\n",
       "413    2\n",
       "414    0\n",
       "415    2\n",
       "416    2\n",
       "417    0\n",
       "Name: Embarked, Length: 418, dtype: int64"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "Y"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "id": "sharp-birthday",
   "metadata": {},
   "outputs": [],
   "source": [
    "from sklearn.model_selection import train_test_split"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "id": "established-activation",
   "metadata": {},
   "outputs": [],
   "source": [
    "X_train, X_test, Y_train, Y_test = train_test_split(X,Y,test_size =0.2)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "id": "confirmed-riverside",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "334"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "len (X_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "id": "tutorial-still",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "84"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "len (X_test)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "id": "crazy-national",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "LinearRegression(copy_X=True, fit_intercept=True, n_jobs=None, normalize=False)"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "clf.fit(X_train,Y_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "specified-graphics",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array([1.36186999, 1.42685395, 1.3993064 , 1.40354448, 1.54975839,\n",
       "       1.37811598, 1.31242568, 1.34986209, 1.25874328, 1.52644892,\n",
       "       1.27922735, 1.47700461, 1.51090928, 1.38235406, 1.33149705,\n",
       "       1.25803693, 1.35127478, 1.3187828 , 1.41555239, 1.51302832,\n",
       "       1.27075118, 1.52150449, 1.3067749 , 1.45581419, 1.48759982,\n",
       "       1.46005227, 1.49042521, 1.39083023, 1.5066712 , 1.44239359,\n",
       "       1.52362353, 1.29688603, 1.38094137, 1.4529888 , 1.44168724,\n",
       "       1.35975095, 1.34774304, 1.51585371, 1.30465585, 1.27781466,\n",
       "       1.52221084, 1.48406808, 1.37670328, 1.41767143, 1.35410017,\n",
       "       1.53916318, 1.31171933, 1.48971886, 1.42261586, 1.29971142,\n",
       "       1.28205274, 1.37175885, 1.47629826, 1.27498927, 1.26227501,\n",
       "       1.28629082, 1.39577466, 1.4932506 , 1.32725897, 1.30394951,\n",
       "       1.50243311, 1.37882233, 1.29759238, 1.47206018, 1.36822712,\n",
       "       1.32655262, 1.33290975, 1.34491765, 1.54269491, 1.46923479,\n",
       "       1.39860005, 1.345624  , 1.28982256, 1.36328269, 1.35268747,\n",
       "       1.36257634, 1.46429036, 1.35056843, 1.49254425, 1.4247349 ,\n",
       "       1.44804437, 1.41484604, 1.27287022, 1.4918379 ])"
      ]
     },
     "execution_count": 23,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "clf.predict(X_test)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "exterior-address",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "151    0\n",
       "243    2\n",
       "204    2\n",
       "210    2\n",
       "417    0\n",
       "      ..\n",
       "240    0\n",
       "273    1\n",
       "226    2\n",
       "25     2\n",
       "335    2\n",
       "Name: Embarked, Length: 84, dtype: int64"
      ]
     },
     "execution_count": 24,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "Y_test"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "ideal-testament",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.010076028902430423"
      ]
     },
     "execution_count": 25,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "clf.score(X_train,Y_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "colonial-czech",
   "metadata": {},
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
   "version": "3.7.8"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
I Have also submitted an .ipynb (code file) in the as03 Folder, Kindly Check it thanks!
