set(comp_sources ThermoLimiter.cpp ../SoftErrorLimiter/beep.cpp ../Stabilizer/TwoDofController.cpp)
set(libs hrpModel-3.1 hrpUtil-3.1 hrpsysBaseStub)
add_library(ThermoLimiter SHARED ${comp_sources})
target_link_libraries(ThermoLimiter ${libs})
set_target_properties(ThermoLimiter PROPERTIES PREFIX "")

add_executable(ThermoLimiterComp ThermoLimiterComp.cpp ${comp_sources})
target_link_libraries(ThermoLimiterComp ${libs})

set(target ThermoLimiter ThermoLimiterComp)

install(TARGETS ${target}
  RUNTIME DESTINATION bin CONFIGURATIONS Release Debug
  LIBRARY DESTINATION lib CONFIGURATIONS Release Debug
)
