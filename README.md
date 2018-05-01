# HTT_AC
HTT AC code

setup

    cmsrel CMSSW_8_1_0
    cd CMSSW_8_1_0/src 
    cmsenv
    git clone https://github.com/senka/HTT_AC_81X.git .
    cp /afs/cern.ch/user/s/senka/public/forAlexis/GitVersion.h CombineHarvester/CombineTools/interface/ # due to issue with github app
    scramv1 b # compiling in paralel does not work

cards need to be copied (from UW) in dir /CombineHarvester/HTTAC2017/shapes/USCMS/:
     
     cp /hdfs/store/user/senka/HTT_stuff/datacards_81/* CombineHarvester/HTTAC2017/shapes/USCMS/


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

code to run limits:

    cp /afs/cern.ch/user/s/senka/public/forYurii/run* .
    source run_1D_fa3_exp # run exp fa3 scans
    source run_1D_fa3_OBS # run obs fa3 scans
    source run_1D_muV_for_fa3_exp # run muV exp scans
    source run_1D_muV_for_fa3_OBS # run muV obs scans
    source run_1D_muf_for_fa3_exp # run muf exp scans
    source run_1D_muf_for_fa3_OBS # run muf obs scans


# Running fa2 limits:


    newFolder=AC_fa2
    MorphingSM2016_D0merged_DCP_fa2_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true
    cd output/AC_fa2
    combineTool.py -M T2W -i {cmb,em,et,mt,tt}/* -o workspace.root --parallel 18
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU_rw:FA2_Interference_JHU_rw -i tt/125/combined.txt.cmb -o fa03_Interference_Workspace_tt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU_rw:FA2_Interference_JHU_rw -i mt/125/combined.txt.cmb -o fa03_Interference_Workspace_mt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU_rw:FA2_Interference_JHU_rw -i et/125/combined.txt.cmb -o fa03_Interference_Workspace_et.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FA2_Interference_JHU_rw:FA2_Interference_JHU_rw -i cmb/125/combined.txt.cmb -o fa03_Interference_Workspace_cmb.root
    
    cp /afs/cern.ch/user/s/senka/public/forYurii/run* .
    source run_1D_fa2_fL1_fL1Zg_exp # run exp fa2 scans
    source run_1D_fa2_fL1_fL1Zg_OBS # run obs fa2 scans
    source run_1D_muV_exp # run muV exp scans
    source run_1D_muV_OBS # run muV obs scans
    source run_1D_muf_exp # run muf exp scans
    source run_1D_muf_OBS # run muf obs scans

# Running fL1 limits:


    newFolder=AC_fL1
    MorphingSM2016_D0merged_DCP_fL1_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true
    cd output/AC_fL1
    combineTool.py -M T2W -i {cmb,em,et,mt,tt}/* -o workspace.root --parallel 18
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1_Interference_JHU_rw:FL1_Interference_JHU_rw -i tt/125/combined.txt.cmb -o fa03_Interference_Workspace_tt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1_Interference_JHU_rw:FL1_Interference_JHU_rw -i mt/125/combined.txt.cmb -o fa03_Interference_Workspace_mt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1_Interference_JHU_rw:FL1_Interference_JHU_rw -i et/125/combined.txt.cmb -o fa03_Interference_Workspace_et.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1_Interference_JHU_rw:FL1_Interference_JHU_rw -i em/125/combined.txt.cmb -o fa03_Interference_Workspace_em.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1_Interference_JHU_rw:FL1_Interference_JHU_rw -i cmb/125/combined.txt.cmb -o fa03_Interference_Workspace_cmb.root
    cp /afs/cern.ch/user/s/senka/public/forYurii/run* .
    source run_1D_fa2_fL1_fL1Zg_exp # run exp fL1 scans
    source run_1D_fa2_fL1_fL1Zg_OBS # run obs fL1 scans
    source run_1D_muV_exp # run muV exp scans
    source run_1D_muV_OBS # run muV obs scans
    source run_1D_muf_exp # run muf exp scans
    source run_1D_muf_OBS # run muf obs scans

# Running fL1Zg limits:


    newFolder=AC_fL1Zg
    MorphingSM2016_D0merged_DCP_fL1Zg_rw --output_folder=${newFolder} --postfix="-Apr7" --control_region=1 --manual_rebin=false --real_data=true --mm_fit=false --ttbar_fit=true
    cd output/AC_fL1Zg
    combineTool.py -M T2W -i {cmb,em,et,mt,tt}/* -o workspace.root --parallel 18
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1Zg_Interference_JHU_rw:FL1Zg_Interference_JHU_rw -i tt/125/combined.txt.cmb -o fa03_Interference_Workspace_tt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1Zg_Interference_JHU_rw:FL1Zg_Interference_JHU_rw -i mt/125/combined.txt.cmb -o fa03_Interference_Workspace_mt.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1Zg_Interference_JHU_rw:FL1Zg_Interference_JHU_rw -i et/125/combined.txt.cmb -o fa03_Interference_Workspace_et.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1Zg_Interference_JHU_rw:FL1Zg_Interference_JHU_rw -i em/125/combined.txt.cmb -o fa03_Interference_Workspace_em.root
    combineTool.py -M T2W -m 125 -P HiggsAnalysis.CombinedLimit.FL1Zg_Interference_JHU_rw:FL1Zg_Interference_JHU_rw -i cmb/125/combined.txt.cmb -o fa03_Interference_Workspace_cmb.root
    source run_1D_fa2_fL1_fL1Zg_exp # run exp fL1Zg scans
    source run_1D_fa2_fL1_fL1Zg_OBS # run obs fL1Zg scans
    source run_1D_muV_exp # run muV exp scans
    source run_1D_muV_OBS # run muV obs scans
    source run_1D_muf_exp # run muf exp scans
    source run_1D_muf_OBS # run muf obs scans


# files with running limits commands:
for 1D scans:
    /afs/cern.ch/user/s/senka/public/forYurii/run*
    
for 2D scan (fa3):
    
    python ../../AC_kappaV_Multithreading_FITTER_exp_ggH_6k.py

for 2D scan (fa2):

    python ../../AC_kappaV_Multithreading_FITTER_exp_6k.py
    
hadd outputs and plot:

    python ../../CombineHarvester/scripts/plotMultiDimFit_CVAC_fa3.py higgsCombineCvAC_FITTER_exp_m0p1to0p1_6k.0to7.MultiDimFit.mH125.root --x-title #mu_{V} --y-title f_{a3} --sm-exp SM_EXP --cms-sub ""


# commands to run GOF:
   /afs/cern.ch/user/s/senka/public/forYurii/do_GOF_anomalous_*

# commands to run impacts:
   /afs/cern.ch/user/s/senka/public/forYurii/do_impacts
