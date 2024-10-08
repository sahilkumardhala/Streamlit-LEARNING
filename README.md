# Streamlit-LEARNING
![Streamlit-LEARNING-iamge](streamlitlogo.png)

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://demo-st-learning-sahil.streamlit.app/)

# Abouts:

Streamlit is an open-source app framework designed for creating and deploying data-driven web applications quickly and easily, using only Python scripts. It allows developers to transform data scripts into interactive and beautiful apps without the need for front-end experience. To start using Streamlit, you first need to install it via pip with `pip install streamlit`. Once installed, you can run a Streamlit app by executing the command `streamlit run your_script.py`. Streamlit offers a range of commands and widgets that make building interactive applications straightforward. Some of the essential commands include `st.title()` for setting the app title, `st.header()` and `st.subheader()` for different levels of headings, and `st.text()` for adding simple text. For displaying data, you can use `st.write()`, which automatically formats your data depending on its type, or `st.dataframe()` for interactive tables. You can also create various input widgets like `st.button()`, `st.slider()`, `st.selectbox()`, and `st.text_input()` to capture user input. Additionally, Streamlit supports charting libraries like Matplotlib, Plotly, and Altair through commands such as `st.pyplot()` and `st.plotly_chart()`. Once your app is ready, you can share it with others by deploying it to a web server, or using `Streamlit Cloud` for hosting. Streamlit’s simplicity and versatility make it an excellent choice for data scientists and engineers looking to create web applications efficiently.

Author:
* @sahilkumardhala : https://github.com/sahilkumardhala/sahilkumardhala


# Deployments
[Streamlit-LEARNING - Sharing for Streamlit](https://demo-st-learning-sahil.streamlit.app/)

# Show me
![Streamlit-LEARNING-iamge](demo.jpg)

---

# All content

## All commands

```python
# All Magic commands simplicitly `st.write()`
''' _This_ is some __Markdown__ '''
a=3
'dataframe:', data
```


## Display text

```python
st.text('Fixed width text')
st.markdown('_Markdown_') # see #*
st.caption('Balloons. Hundreds of them...')
st.latex(r\'\'\' e^{i\pi} + 1 = 0 \'\'\')
st.write('Most objects') # df, err, func, keras!
st.write(['st', 'is <', 3]) # see *
st.title('My title')
st.header('My header')
st.subheader('My sub')
st.code('for i in range(8): foo()')

# * optional kwarg unsafe_allow_html = True
```


## Display data

```python
st.dataframe(my_dataframe)
st.table(data.iloc[0:10])
st.json({'foo':'bar','fu':'ba'})
st.metric(label="Temp", value="273 K", delta="1.2 K")
```


## Display media

```python
st.image('./header.png')
st.audio(data)
st.video(data)
```


## Columns

```python
col1, col2 = st.columns(2)
col1.write('Column 1')
col2.write('Column 2')

# Three columns with different widths
col1, col2, col3 = st.columns([3,1,1])
# col1 is wider
              
# Using 'with' notation:
>>> with col1:
>>>     st.write('This is column 1')
```


## Tabs

```python
# Insert containers separated into tabs:
>>> tab1, tab2 = st.tabs(["Tab 1", "Tab2"])
>>> tab1.write("this is tab 1")
>>> tab2.write("this is tab 2")

# You can also use "with" notation:
>>> with tab1:
>>>   st.radio('Select one:', [1, 2])
```


## Control flow
```python
# Stop execution immediately:
st.stop()
# Rerun script immediately:
st.experimental_rerun()

# Group multiple widgets:
>>> with st.form(key='my_form'):
>>>   username = st.text_input('Username')
>>>   password = st.text_input('Password')
>>>   st.form_submit_button('Login')
```


## Personalize apps for users

```python
# Show different content based on the user's email address.
>>> if st.user.email == 'jane@email.com':
>>>    display_jane_content()
>>> elif st.user.email == 'adam@foocorp.io':
>>>    display_adam_content()
>>> else:
>>>    st.write("Please contact us to get access!")
```


## Display interactive widgets

```python
st.button('Hit me')
st.data_editor('Edit data', data)
st.checkbox('Check me out')
st.radio('Pick one:', ['nose','ear'])
st.selectbox('Select', [1,2,3])
st.multiselect('Multiselect', [1,2,3])
st.slider('Slide me', min_value=0, max_value=10)
st.select_slider('Slide to select', options=[1,'2'])
st.text_input('Enter some text')
st.number_input('Enter a number')
st.text_area('Area for textual entry')
st.date_input('Date input')
st.time_input('Time entry')
st.file_uploader('File uploader')
st.download_button('On the dl', data)
st.camera_input("一二三,茄子!")
st.color_picker('Pick a color')

# Use widgets\' returned values in variables
>>> for i in range(int(st.number_input('Num:'))): foo()
>>> if st.sidebar.selectbox('I:',['f']) == 'f': b()
>>> my_slider_val = st.slider('Quinn Mallory', 1, 88)
>>> st.write(slider_val)

# Disable widgets to remove interactivity:
>>> st.slider('Pick a number', 0, 100, disabled=True)
```


## Build chat-based apps

```python
# Insert a chat message container.
>>> with st.chat_message("user"):
>>>    st.write("Hello 👋")
>>>    st.line_chart(np.random.randn(30, 3))

# Display a chat input widget.
>>> st.chat_input("Say something")  
```

## Mutate data

```python
# Add rows to a dataframe after showing it.
>>> element = st.dataframe(df1)
>>> element.add_rows(df2)

# Add rows to a chart after showing it.
>>> element = st.line_chart(df1)
>>> element.add_rows(df2)
```

## Display code

```python
st.echo()
>>> with st.echo():
>>>     st.write('Code will be executed and printed')
```


## Placeholders, help, and options

```python
# Replace any single element.
>>> element = st.empty()
>>> element.line_chart(...)
>>> element.text_input(...)  # Replaces previous.

# Insert out of order.
>>> elements = st.container()
>>> elements.line_chart(...)
>>> st.write("Hello")
>>> elements.text_input(...)  # Appears above "Hello".

st.help(pandas.DataFrame)
st.get_option(key)
st.set_option(key, value)
st.set_page_config(layout='wide')
st.experimental_show(objects)
st.experimental_get_query_params()
st.experimental_set_query_params(**params)
```


## Connect to data sources

```python
st.experimental_connection('pets_db', type='sql')
conn = st.experimental_connection('sql')
conn = st.experimental_connection('snowpark')

>>> class MyConnection(ExperimentalBaseConnection[myconn.MyConnection]):
>>>    def _connect(self, **kwargs) -> MyConnection:
>>>        return myconn.connect(**self._secrets, **kwargs)
>>>    def query(self, query):
>>>       return self._instance.query(query)
```


## Optimize performance

### Cache data objects

```python
# E.g. Dataframe computation, storing downloaded data, etc.
>>> @st.cache_data
... def foo(bar):
...   # Do something expensive and return data
...   return data
# Executes foo
>>> d1 = foo(ref1)
# Does not execute foo
# Returns cached item by value, d1 == d2
>>> d2 = foo(ref1)
# Different arg, so function foo executes
>>> d3 = foo(ref2)
# Clear all cached entries for this function
>>> foo.clear()
# Clear values from *all* in-memory or on-disk cached functions
>>> st.cache_data.clear()
```

### Cache global resources

```python
# E.g. TensorFlow session, database connection, etc.
>>> @st.cache_resource
... def foo(bar):
...   # Create and return a non-data object
...   return session
# Executes foo
>>> s1 = foo(ref1)
# Does not execute foo
# Returns cached item by reference, s1 == s2
>>> s2 = foo(ref1)
# Different arg, so function foo executes
>>> s3 = foo(ref2)
# Clear all cached entries for this function
>>> foo.clear()
# Clear all global resources from cache
>>> st.cache_resource.clear()
```

### Deprecated caching

```python
>>> @st.cache
... def foo(bar):
...   # Do something expensive in here...
...   return data
>>> # Executes foo
>>> d1 = foo(ref1)
>>> # Does not execute foo
>>> # Returns cached item by reference, d1 == d2
>>> d2 = foo(ref1)
>>> # Different arg, so function foo executes
>>> d3 = foo(ref2)
```

## Display progress and status

```python
# Show a spinner during a process
>>> with st.spinner(text='In progress'):
>>>   time.sleep(3)
>>>   st.success('Done')

# Show and update progress bar
>>> bar = st.progress(50)
>>> time.sleep(3)
>>> bar.progress(100)

st.balloons()
st.snow()
st.toast('Mr Stay-Puft')
st.error('Error message')
st.warning('Warning message')
st.info('Info message')
st.success('Success message')
st.exception(e)
```

### Other key parts of the API
<small>[State API](https://docs.streamlit.io/en/stable/session_state_api.html)</small><br>
<small>[Theme option reference](https://docs.streamlit.io/en/stable/theme_options.html)</small><br>
<small>[Components API reference](https://docs.streamlit.io/en/stable/develop_streamlit_components.html)</small><br>

---