1. Idea: Model local part appearances, and spatial relationships between parts
2. Model $M$ with parts $V=\{v_1, v_2, \cdots, v_m\}$
	1. object configuration $L = (l_1,\cdots,l_m)$
	2. goal: given image $I$, find configurations that maximize $P(L|I,M)$
	3. if part apperance are independent, from Baye's law, $P(L|I,M)\propto P(L|M)\prod_{v_i\in V}P(I|l_i,M)$
