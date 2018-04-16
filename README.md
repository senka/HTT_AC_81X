# HTT_AC
HTT AC code

# Running fa3 limits:

creating datacards

    newFolder=AC_fa3
    MorphingSM2016_D0merged_DCP_ggHSyst_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true


create combined cards and workspaces:

    cd output/AC_fa3
    combineTool.py -M T2W -i {cmb,em,et,mt,tt}/* -o workspace.root --parallel 18
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA3_Interference_JHU_ggHSyst_rw:FA3_Interference_JHU_ggHSyst_rw -i tt/125/combined.txt.cmb -o fa03_Interference_Workspace_tt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA3_Interference_JHU_ggHSyst_rw:FA3_Interference_JHU_ggHSyst_rw -i mt/125/combined.txt.cmb -o fa03_Interference_Workspace_mt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA3_Interference_JHU_ggHSyst_rw:FA3_Interference_JHU_ggHSyst_rw -i et/125/combined.txt.cmb -o fa03_Interference_Workspace_et.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA3_Interference_JHU_ggHSyst_rw:FA3_Interference_JHU_ggHSyst_rw -i em/125/combined.txt.cmb -o fa03_Interference_Workspace_em.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA3_Interference_JHU_ggHSyst_rw:FA3_Interference_JHU_ggHSyst_rw -i cmb/125/combined.txt.cmb -o fa03_Interference_Workspace_cmb.root


# Running fa2 limits:
differences wrt running fa3 are:

    MorphingSM2016_D0merged_DCP_fa2_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true

    ...
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU:FA2_Interference_JHU -i tt/125/combined.txt.cmb -o fa03_Interference_Workspace_tt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU:FA2_Interference_JHU -i mt/125/combined.txt.cmb -o fa03_Interference_Workspace_mt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU:FA2_Interference_JHU -i et/125/combined.txt.cmb -o fa03_Interference_Workspace_et.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU:FA2_Interference_JHU -i cmb/125/combined.txt.cmb -o fa03_Interference_Workspace_cmb.root

# Running fL1 limits:
differences wrt running fa3 are:

    MorphingSM2016_D0merged_DCP_fL1_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true

# Running fL1Zg limits:
differences wrt running fa3 are:

    MorphingSM2016_D0merged_DCP_fL1Zg_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true


# files with running limits commands:
for 1D scans:
    /afs/cern.ch/user/s/senka/public/forYurii/run*
    
for 2D scan (fa3):
    
    python ../../AC_kappaV_Multithreading_FITTER_exp_ggH_6k.py

for 2D scan (fa2):

    python ../../AC_kappaV_Multithreading_FITTER_exp_6k.py
    
hadd outputs and plot:

    python ../../CombineHarvester/scripts/plotMultiDimFit_CVAC_fa3.py higgsCombineCvAC_FITTER_exp_m0p1to0p1_6k.0to7.MultiDimFit.mH125.root --x-title #mu_{V} --y-title f_{a3} --sm-exp SM_EXP --cms-sub ""


# datacards location ---> cards need to be copied in dir /CombineHarvester/HTTAC2017/shapes/USCMS/:
    /hdfs/store/user/senka/HTT_stuff/datacards_81/
