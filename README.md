from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.button import Button
from kivy.core.window import Window
from kivy.uix.screenmanager import ScreenManager,Screen
from kivy.uix.image import Image
Window.clearcolor = (1, 1, 1, 1)
class MenuScreen(Screen):
    def __init__(self,**kw):
        super(MenuScreen,self).__init__(**kw)
        self.box = BoxLayout(orientation = 'vertical')
        self.box2 = BoxLayout(orientation = 'horizontal')
        self.box.add_widget(self.box2)
        self.add_widget(Label(text ='категории',color = (255,255,255),pos_hint = {'x':0.1} ))
        self.box.add_widget(Button(text = '',on_press = lambda x: set_screen('food_screen'), pos_hint = {'top':1,'x':0.35},background_normal = 'food.net.jpeg', size_hint= (0.3,0.5)))
        self.box.add_widget(Label(text = 'еда',color = (255,255,255)))
        self.box.add_widget(Button(text='', on_press=lambda x: set_screen('music_screen'), background_normal = "musica.net.jpeg", size_hint= (0.3,0.5), pos_hint= {'x':0.35}))
        self.box.add_widget(Label(text='музыка',color = (255,255,255)))
        self.box.add_widget(Button(text='', on_press=lambda x: set_screen('kubik_screen'), pos_hint= {'bottom':1,'x':0.35},background_normal = "kubik.net.jpeg", size_hint= (0.3,0.5) ))
        self.box.add_widget(Label(text='бросить кубик',color = (255,255,255)))
        self.add_widget(self.box)
class Food(Screen):
    def __init__(self,**kw):
        super(Food,self).__init__(**kw)
        self.box = BoxLayout(orientation = 'vertical')
        self.box2 = BoxLayout(orientation = 'horizontal')
        self.back_button = Button(text = '', on_press = lambda x: set_screen('menu'))
        self.image = Image(source = 'кот.png')
        self.box.add_widget(self.back_button)
        self.box.add_widget(self.image)
        self.add_widget(self.box)
def set_screen(name_screen):
    sm.current = name_screen
sm = ScreenManager()
sm.add_widget(MenuScreen(name='menu'))
class MyApp(App):
    def build(self):
        return sm
if __name__ == '__main__':
    MyApp().run()
