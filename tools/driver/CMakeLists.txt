set(LLVM_LINK_COMPONENTS
Support
)
add_sreelang_tool(sreelang
Calc.cpp
)
target_link_libraries(sreelang
PRIVATE
sreelangBasic
)
target_link_libraries(sreelang PRIVATE ${llvm_libs})