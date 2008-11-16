INCLUDE_DIRECTORIES( ${GLUI_INCLUDE_DIR} ${GLUT_INCLUDE_DIR} ${LIBNIFALCON_INCLUDE_DIRS}/falcon ${ODE_INCLUDE_DIR} ${Boost_INCLUDE_DIRS} )
LINK_DIRECTORIES(${Boost_LIBRARY_DIRS} ${CMAKE_CURRENT_SOURCE_DIR}/../../lib)

ADD_EXECUTABLE(falcon_mechanics
  main.cpp 
  view/Viewer.cpp 
  view/Toolbox.cpp 
  view/falcon/Falcon.cpp 
  view/falcon/Element.cpp 
  view/falcon/Arm.cpp
  view/falcon/Base.cpp
  view/falcon/Effector.cpp
  view/falcon/Joint.cpp
  view/falcon/Parallel.cpp
  view/falcon/Force.cpp
  controller/Controller.cpp)

TARGET_LINK_LIBRARIES(falcon_mechanics
  ${OSG_LIBRARY}
  ${OSGVIEWER_LIBRARY}
  ${OSGGA_LIBRARY}
  ${OSGDB_LIBRARY}
  ${OSGTEXT_LIBRARY}
  ${OSGFX_LIBRARY}
  ${GLUI_LIBRARIES}
  ${ODE_LIBRARY}
  ${Boost_LIBRARIES}
  ${GLUT_glut_LIBRARY}
  ${LIBNIFALCON_LIBRARIES}
  ${LIBNIFALCON_COMM_LIBRARIES}
  ${LIBNIFALCON_DEVICE_BOOST_THREAD_LIBRARY}
  )

SET(CMAKE_CXX_FLAGS_RELEASE -O3)

#IF(UNIX AND NOT APPLE)
  TARGET_LINK_LIBRARIES(falcon_mechanics m ${GLUT_glut_LIBRARY} ${GLUI_LIBRARIES} ${ODE_LIBRARY} ${Boost_LIBRARIES}) 
#ENDIF(UNIX )
#IF(APPLE)
#  TARGET_LINK_LIBRARIES(falcon m ${ODE_LIBRARY} ${Boost_LIBRARIES} ${GLUI_LIBRARIES}) 
#  SET_TARGET_PROPERTIES(falcon_mechanics PROPERTIES LINK_FLAGS "-framework OpenGL -framework IOKit -framework Carbon -framework GLUT -framework GLUI")
#ENDIF(APPLE)