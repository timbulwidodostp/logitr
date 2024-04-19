# # Olah Data Semarang
# # WhatsApp : +6285227746673
# # IG : @olahdatasemarang_
# # The main function for estimating logit models Use Package logitr With (In) R Software
# # Logit Models w/Preference & WTP Space Utility Parameterizations Use Package logitr With (In) R Software
# # Fast Estimation of Multinomial and Mixed Logit Models with Preference Space and Willingness to Pay Space Utility Parameterizations 
#   Use Package logitr With (In) R Software
install.packages("logitr")
library("logitr")
# # Import Data Excel Into R From Github Olah Data Semarang (timbulwidodostp)
github_link <- "https://github.com/timbulwidodostp/logitr/raw/main/logitr/logitr.xlsx"
temp_file <- tempfile(fileext = ".xlsx")
req <- GET(github_link, 
# # authenticate using GITHUB_PAT
authenticate(Sys.getenv("GITHUB_PAT"), ""),
# # write result to disk
write_disk(path = temp_file))
logitr <- readxl::read_excel(temp_file)
# # Estimate The main function for estimating logit models Use Package logitr With (In) R Software
# # Estimate a MNL model in the Preference space
mnl_pref<-logitr(data =logitr,outcome ="choice",obsID ="obsID",pars=c("price","feat","brand"))
summary(mnl_pref)
# # Estimate a MNL model in the WTP space, using a 5-run multistart
mnl_wtp <-logitr(data=logitr,outcome="choice",obsID="obsID",pars=c("feat","brand"),scalePar="price",numMultiStarts=5)
summary(mnl_wtp)
# # Estimate a MXL model in the Preference space with "feat"
# # following a normal distribution
# # Panel structure is accounted for in this example using "panelID"
mxl_pref<-logitr(data=logitr,outcome="choice",obsID= "obsID",panelID="id",pars=c("price","feat","brand"),randPars=c(feat="n"))
summary(mxl_pref)
# # The main function for estimating logit models Use Package logitr With (In) R Software
# # Logit Models w/Preference & WTP Space Utility Parameterizations Use Package logitr With (In) R Software
# # Fast Estimation of Multinomial and Mixed Logit Models with Preference Space and Willingness to Pay Space Utility Parameterizations 
#   Use Package logitr With (In) R Software
# # Olah Data Semarang
# # WhatsApp : +6285227746673
# # IG : @olahdatasemarang_
# # Finished