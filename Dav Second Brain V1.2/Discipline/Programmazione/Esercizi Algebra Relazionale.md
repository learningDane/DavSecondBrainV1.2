#uni 
1. trovare matricola, nome, età e stipendio degli impiegati che guadagnano più di 40
   : $$ \pi_{matricola, nome, età, stipendio}(\sigma_{stipendio > 40}(impiegati))$$
2. trovare il capo degli impiegati che guadagnano più di 40
   : $$ \pi_{capo}(\sigma_{stipendio > 40}({impiegati \bowtie_{matricola=impiegato}supervisione}))$$
3. trovare nome e stipendio dei capi degli impiegati che guadagnano più di 40
   : $$\pi_{nome, stipendio}(impiegati \bowtie_{matricola = capo} (\pi_{capo}(\sigma_{stipendio > 40}(impiegati\bowtie supervisione)$$
4. trovare gli impiegati che guadagnano più del proprio capo, mostrando matricola, nome e stipendio dell'impiegato e del capo
   : $$\sigma_{stipendio>stipcap}(impiegato \bowtie_{impiegato=matricola}(\rho_{matcap,nomcap,stipcap\leftarrow matricola,nome,stipendio}(\pi_{matricola,nome,stipendio,impiegato}(supervisione \bowtie_{capo=matricola}impiegati))))$$
   ![[Pasted image 20240814002503.png]]