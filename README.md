# React-Native-Image-Capture

![](https://aboutreact.com/wp-content/uploads/2018/07/react_native_camera-1.png)

# Steps:

* First of create new project 
   
      $ react-native init projectname
   
   
* After successfull create project to run application

      $ react-native run-android
      $ react-native run-ios
      
* Make changes for App.js file


      import React from 'react'
      import { View, Image, StyleSheet, TouchableOpacity, ScrollView, Text } from 'react-native'
      import ImagePicker from 'react-native-image-picker'

      export default class App extends React.Component {
          constructor() {
              super()
              this.state = { imageSource: { uri:                       'https://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/No_image_available_400_x_600.svg/2000px-   No_image_available_400_x_600.svg.png' },
                  }
              }

        selectPhoto = () => {
            const options = {
                title: 'Select a option',
                takePhotoButtonTitle: 'Take a photo',
                chooselibraryButtonTitle: 'Choose from Gallery',
                quality: 1
            }

        ImagePicker.showImagePicker(options, (response) => {
            console.log('Respose = ', response);

            if (response.didCancel) {
                console.log('User cancelled image picker');
            }

            else if (response.error) {
                console.log('ImagePicker Error: ', response.error);
            }
            else {
                let source = { uri: response.uri };
                this.setState({
                            imageSource: source
                        })
                    }
                })
            }
            render() {
                return (
                    <ScrollView style={{ backgroundColor: '#fff' }}>

                        <View style={styles.container}>

                    <View style={{ alignItems: 'center', height: 60, 
                    backgroundColor: 'lightblue', flex: 0.1, justifyContent: 'center' }}>
                        <Text style={{ fontSize: 23, fontWeight: 'bold' }}>Image Capture  </Text>
                    </View>

                    <View style={{ flex: 0.9, alignItems: 'center' }}>

                        <Image
                            style={{ width: 300, height: 300, marginTop: 20, marginBottom: 5 }}
                            source={this.state.imageSource}
                        />

                        <TouchableOpacity style={styles.button} onPress={this.selectPhoto.bind(this)}>

                            <Text style={{ fontSize: 18, fontWeight: 'bold' }}> Click Here </Text>

                        </TouchableOpacity>

                    </View>

                          </View>
                      </ScrollView>
                  )
              }
          }

          const styles = StyleSheet.create({
              container: {
                  flex: 1,
                  backgroundColor: '#fff'
              },
              button: {
                  width: 220,
                  height: 50,
                  borderRadius: 7,
                  marginTop: 20,
                  marginBottom: 20,
                  backgroundColor: 'lightblue',
                  alignItems: 'center',
                  justifyContent: 'center'
              },
          })


