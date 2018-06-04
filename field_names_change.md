This is to change part of the field name in a table. Here I am changing the 'YearCEAdd19'.


``` py
import arcpy

gdb =r"C:\Users\admin\Box Sync\CE_Project\Washington_SO\compiling\data\spatial\WAS_data_prep.gdb"
tbl = "Tbl_CEProx"
tblpath = gdb + "\\" + tbl

##fieldList = [f.name for f in arcpy.ListFields(tblpath)]
##nlist = filter(lambda k: 'YearCEAdd' in k, fieldList)
##blist = [w.replace("YearCEAdd19","CEProx") for w in nlist]
##blist = [w.replace("YearCEAdd20","CEProx") for w in blist]

##fc = r'path to your feature class'
flds = arcpy.ListFields(tblpath, field_type="Long")

for fld in flds:
    if fld.name.startswith("YearCEAdd19"):
        arcpy.AlterField_management(tblpath, fld.name, fld.name.replace("YearCEAdd19","CEProx"), fld.name.replace("YearCEAdd19","CEProx"))

for fld in flds:
    if fld.name.startswith("YearCEAdd20"):
        arcpy.AlterField_management(tblpath, fld.name, fld.name.replace("YearCEAdd20","CEProx"), fld.name.replace("YearCEAdd20","CEProx"))
```
        
