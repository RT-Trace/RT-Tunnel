import os
from building import *

objs = [] 
cwd = GetCurrentDir() 

src = Glob('*.c')  
current_group = DefineGroup('RT_TUNNEL', src, depend=[], CPPPATH=[cwd])
objs.append(current_group) 

subdirs = os.listdir(cwd) 
for item in subdirs:
    subdir_path = os.path.join(cwd, item)
    if os.path.isdir(subdir_path) and os.path.exists(os.path.join(subdir_path, 'SConscript')):
        sub_group = SConscript(os.path.join(item, 'SConscript'))
        objs.extend(sub_group if isinstance(sub_group, list) else [sub_group])

Return('objs')