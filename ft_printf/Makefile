# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: zabderra <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2022/03/16 16:12:57 by zabderra          #+#    #+#              #
#    Updated: 2022/03/21 18:40:27 by zabderra         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

#Variables

NAME		= libftprintf.a
INCLUDE		= include
LIBFT		= libft
SRC_DIR		= src/
OBJ_DIR		= obj/
CC			= gcc
CFLAGS		= -Wall -Werror -Wextra -I
RM			= rm -f
AR			= ar rcs

#Sources

SRC_FILES	=	ft_printf ft_printf_utils ft_print_ptr ft_print_unsigned ft_print_hex


SRC 		= 	$(addprefix $(SRC_DIR), $(addsuffix .c, $(SRC_FILES)))
OBJ 		= 	$(addprefix $(OBJ_DIR), $(addsuffix .o, $(SRC_FILES)))

###

OBJF		=	.cache_exists

all:		$(NAME)

$(NAME):	$(OBJ)
			@make -C $(LIBFT)
			@cp libft/libft.a .
			@mv libft.a $(NAME)
			@$(AR) $(NAME) $(OBJ)
			@echo "ft_printf compiled!"

$(OBJ_DIR)%.o: $(SRC_DIR)%.c | $(OBJF)
			@echo "Compiling: $<"
			@$(CC) $(CFLAGS) $(INCLUDE) -c $< -o $@

$(OBJF):
			@mkdir -p $(OBJ_DIR)

clean:
			@$(RM) -rf $(OBJ_DIR)
			@make clean -C $(LIBFT)
			@echo "ft_printf object files cleaned!"

fclean:		clean
			@$(RM) -f $(NAME)
			@$(RM) -f $(LIBFT)/libft.a
			@echo "ft_printf executable files cleaned!"
			@echo "libft executable files cleaned!"

re:			fclean all
			@echo "Cleaned and rebuilt everything for ft_printf!"

norm:
			@norminette $(SRC) $(INCLUDE) $(LIBFT) | grep -v Norme -B1 || true

.PHONY:		all clean fclean re norm