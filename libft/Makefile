# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: hdeniz <Discord:@teomandeniz>              +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2022/10/24 10:48:13 by hdeniz            #+#    #+#              #
#    Updated: 2024/03/02 16:31:01 by hdeniz           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# ************************* [v] SET MAKECMDGOALS [v] ************************* #
#                                                                              #
# IT IS A FIX FOR OVERLINKING, INSTEAD IF CALLING A PHONY TO CALCULATE HOW     #
# MANY .o FILES HAVE, WE DIRECTLY CALCULATING IT IN GLOBAL VARIABLES.          #
#                                                                              #
################################################################################
MAKECMDGOALS	:=	./
# ************************* [^] SET MAKECMDGOALS [^] ************************* #

# *************************** [v] MAIN SOURCES [v] *************************** #
MAIN_SRC	=	./bool/ft_isalnum.c \
				./bool/ft_isalpha.c \
				./bool/ft_isascii.c \
				./bool/ft_isdigit.c \
				./bool/ft_isprint.c \
				./converters/ft_atoi.c \
				./converters/ft_itoa.c \
				./converters/ft_tolower.c \
				./converters/ft_toupper.c \
				./memory/ft_bzero.c \
				./memory/ft_calloc.c \
				./memory/ft_memchr.c \
				./memory/ft_memcmp.c \
				./memory/ft_memcpy.c \
				./memory/ft_memmove.c \
				./memory/ft_memset.c \
				./output/ft_putchar_fd.c \
				./output/ft_putendl_fd.c \
				./output/ft_putnbr_fd.c \
				./output/ft_putstr_fd.c \
				./string/ft_split.c \
				./string/ft_strchr.c \
				./string/ft_strdup.c \
				./string/ft_striteri.c \
				./string/ft_strjoin.c \
				./string/ft_strlcat.c \
				./string/ft_strlcpy.c \
				./string/ft_strlen.c \
				./string/ft_strmapi.c \
				./string/ft_strncmp.c \
				./string/ft_strnstr.c \
				./string/ft_strrchr.c \
				./string/ft_strtrim.c \
				./string/ft_substr.c
# *************************** [^] MAIN SOURCES [^] *************************** #

# ************************** [v] BONUS SOURCES [v] *************************** #
BONUS_SRC	=	./lists/ft_lstadd_back.c \
				./lists/ft_lstadd_front.c \
				./lists/ft_lstclear.c \
				./lists/ft_lstdelone.c \
				./lists/ft_lstiter.c \
				./lists/ft_lstlast.c \
				./lists/ft_lstmap.c \
				./lists/ft_lstnew.c \
				./lists/ft_lstsize.c
# ************************** [^] BONUS SOURCES [^] *************************** #

# ****************************** [v] BONUS [v] ******************************* #
	# [.c STRINGS TO .o]
		BONUS_OBJ	=	./ft_lstadd_back.c \
						./ft_lstadd_front.c \
						./ft_lstclear.c \
						./ft_lstdelone.c \
						./ft_lstiter.c \
						./ft_lstlast.c \
						./ft_lstmap.c \
						./ft_lstnew.c \
						./ft_lstsize.c
	# [.c STRINGS TO .o]
# ****************************** [^] BONUS [^] ******************************* #

# **************************** [v] VARIABLES [v] ***************************** #
	# [COMPILER]
		CC			=	gcc
	# [COMPILER]
	# [ARCHIVE AND OVERLINKING CHECKER]
		NAME		=	./libft.a
	# [ARCHIVE AND OVERLINKING CHECKER]
	# [COMPILER FLAGS]
		CFLAGS		=	-Wall -Wextra -Werror -std=c99 # -g
	# [COMPILER FLAGS]
	# [.c STRINGS TO .o]
		MAIN_OBJ	=	$(MAIN_SRC:.c=.o)
	# [.c STRINGS TO .o]
	# ANIMATION VARIABLES
		TERMINAL_LEN	:=	\
			$(eval TERMINAL_LEN := $(shell tput cols))$(TERMINAL_LEN)
		NUMBER_OF_FILES	:=	0
		FILE_COUNTER	:=	0
		N_OBJ			:=	$(eval N_OBJ := $$(shell find $(MAKECMDGOALS) \
		"./libft" -name '*.o' -type f | wc -w | sed "s/ //g" | bc))$(N_OBJ)
	# ANIMATION VARIABLES
# **************************** [^] VARIABLES [^] ***************************** #

# ****************************** [v] COLORS [v] ****************************** #
	C_RESET	=	$(shell tput sgr0)
	C_BLINK	=	$(shell tput blink)
	F15		=	$(shell tput setaf 15)
	B1F11	=	$(shell tput setab 1)$(shell tput setaf 11)
	B12F15	=	$(shell tput setab 12)$(shell tput setaf 15)
	B1F15	=	$(shell tput setab 1)$(shell tput setaf 15)
	B2F15	=	$(shell tput setab 2)$(shell tput setaf 15)
	F11		=	$(shell tput setaf 11)
	F13		=	$(shell tput setaf 13)
	F14		=	$(shell tput setaf 14)
	F10		=	$(shell tput setaf 10)
	F0		=	$(shell tput setaf 0)
# ****************************** [^] COLORS [^] ****************************** #

# ***************************#* [v] FUNCIONS [v] ***************************** #
define progress_bar
	$(eval PBAR := $(shell echo $(1)*100/$(2)*100/100 | bc))
	$(eval PDONE := $(shell echo $(PBAR)*3/10 | bc))
	$(eval PLEFT := $(shell echo 30-$(PDONE) | bc))
	$(eval PSEQ := $(shell seq 0 1 $(PLEFT) 2>/dev/null))
	$(eval PEMPTY := $(shell if [ "$(1)" -ne "$(2)" ]; \
		then printf ".%.0s" $(PSEQ); fi))
	$(eval PFILL := $(shell printf "\#%.0s" $(shell seq 1 $(PDONE))))
	@printf "\r%*s\r $(F11)[$(F14)$(PFILL)$(PEMPTY)$(F11)] $(PBAR)%% - \
		$(F10)[$(1)/$(2)]$(F11) [$(F13)$(3)$(F11)$(C_RESET)]" \
		$(TERMINAL_LEN) " "
endef
# ***************************#* [^] FUNCIONS [^] ***************************** #

%.o: %.c
	$(eval NUMBER_OF_FILES := $(shell echo $(MAIN_SRC) \
		| wc -w | sed "s/ //g" | bc))
	$(eval NUMBER_OF_FILES := $(shell echo $(NUMBER_OF_FILES) - $(N_OBJ) | bc))
	$(if $(filter 0,$(NUMBER_OF_FILES)), $(eval NUMBER_OF_FILES := 1))
	$(eval FILE_COUNTER := $(shell echo $(FILE_COUNTER) + 1 | bc))
	$(call progress_bar,$(FILE_COUNTER),$(NUMBER_OF_FILES),$<)
	@$(CC) $(CFLAGS) -c $< -o $@ 2>/dev/null || (\
		echo "\n\n $(B1F15) Failed to compile [$(F11)$<$(F15)] $(C_RESET)\n" &&\
		$(CC) $(CFLAGS) -c $< -o $@)

all: $(NAME)

$(NAME): $(MAIN_OBJ)
	@ar -rcs $(NAME) $(MAIN_OBJ) 2>/dev/null && \
		echo "\n\n $(C_BLINK)$(B2F15) $(NAME) is ready! $(C_RESET)\n"

b: bonus
bonus: $(BONUS_OBJ) $(NAME)

c: clean
clear: clean
clean:
	@rm $(MAIN_OBJ) $(BONUS_OBJ) 2>/dev/null && \
		echo "\n $(B1F15) Objects are cleared! $(C_RESET)\n" || \
		echo "\n $(B12F15) Nothing to clear! $(C_RESET)\n"
	$(eval N_OBJ := "0")

fc: fclean
fclean: clean
	@rm $(NAME) 2>/dev/null && \
		echo "\n $(B1F11) $(NAME) $(F15)deleted! $(C_RESET)\n" || \
		echo "\n $(B12F15) $(NAME) is not exist already! $(C_RESET)\n"

re: fc all

.PHONY: all fclean fc clean clear c bonus b
