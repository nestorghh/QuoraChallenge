library(readr)
library(ggplot2)
df3 <- read_csv("quora_challenge/df3_quora.csv", 
                      col_types = cols(X1 = col_skip()))
View(df3)

nrow(df3)

table(df3$variant_number,exclude=NULL)


#boxplot user type
g <- ggplot(df3, aes(user_type, active_mins))
g + geom_boxplot(aes(fill=factor(variant_number)))+
  scale_fill_manual(values=c('#107896','#AA2200'))+
  theme(
    panel.background = element_blank(),
    panel.grid.major =  element_line(colour = "grey",size=0.01,linetype = 8), 
    panel.grid.minor = element_blank(),
    axis.line.x = element_line(colour = "black"),
    axis.line.y = element_line(colour = "black"),
    #legend.background = element_rect(fill="transparent", size=0.5, linetype="solid"),
    #legend.position = c(0.1,0.9),
    legend.text = element_text(colour="black", size=14),
    legend.title=element_text(size=14),
    legend.box = "horizontal",
    axis.text = element_text(colour = "black"),
    axis.text.x = element_text(size = 14,vjust=0.6),
    axis.text.y = element_text(size = 14),
    axis.title = element_text(size = 14),
    strip.text.x = element_text(size = 14)) + labs(x='User Type',y='Active Mins') + guides(fill=guide_legend(title="Treatment"))


#boxplot user gender
g <- ggplot(df3, aes(gender, active_mins))
g + geom_boxplot(aes(fill=factor(variant_number)))+
  scale_fill_manual(values=c('#107896','#AA2200'))+
  theme(
    panel.background = element_blank(),
    panel.grid.major =  element_line(colour = "grey",size=0.01,linetype = 8), 
    panel.grid.minor = element_blank(),
    axis.line.x = element_line(colour = "black"),
    axis.line.y = element_line(colour = "black"),
    #legend.background = element_rect(fill="transparent", size=0.5, linetype="solid"),
    #legend.position = c(0.1,0.9),
    legend.text = element_text(colour="black", size=14),
    legend.title=element_text(size=14),
    legend.box = "horizontal",
    axis.text = element_text(colour = "black"),
    axis.text.x = element_text(size = 14,vjust=0.6),
    axis.text.y = element_text(size = 14),
    axis.title = element_text(size = 14),
    strip.text.x = element_text(size = 14)) + labs(x='User Gender',y='Active Mins') + guides(fill=guide_legend(title="Treatment"))



#boxplot interaction

df3$f1f2 <- interaction(df3$user_type, df3$gender)

g <- ggplot(df3, aes(f1f2, active_mins))
g + geom_boxplot(aes(fill=factor(variant_number)))+
  scale_fill_manual(values=c('#107896','#AA2200'))+
  theme(
    panel.background = element_blank(),
    panel.grid.major =  element_line(colour = "grey",size=0.01,linetype = 8), 
    panel.grid.minor = element_blank(),
    axis.line.x = element_line(colour = "black"),
    axis.line.y = element_line(colour = "black"),
    #legend.background = element_rect(fill="transparent", size=0.5, linetype="solid"),
    #legend.position = c(0.1,0.9),
    legend.text = element_text(colour="black", size=14),
    legend.title=element_text(size=14),
    legend.box = "horizontal",
    axis.text = element_text(colour = "black"),
    axis.text.x = element_text(size = 14,vjust=0.6,angle=90),
    axis.text.y = element_text(size = 14),
    axis.title = element_text(size = 14),
    strip.text.x = element_text(size = 14)) + labs(x='User Type-Gender',y='Active Mins') + guides(fill=guide_legend(title="Treatment"))
